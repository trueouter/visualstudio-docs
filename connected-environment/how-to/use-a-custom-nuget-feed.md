---
title: "How to use a custom NuGet feed in a connected environment| Microsoft Docs"
author: "johnsta"
ms.author: "johnsta"
ms.date: "03/27/2018"
ms.topic: "article"
description: "Use a custom NuGet feed to access and use NuGet packages in a connected environment."
keywords: "Docker, Kubernetes, Azure, AKS, Azure Container Service, containers"
manager: "ghogen"
---
#  Use a custom NuGet feed in a connected environment

A NuGet feed provides a convenient way to include package sources in a project. Connected Environment will need to be able to access this feed in order for dependencies to be properly installed in the Docker container.

To set up a NuGet feed:
1. Add a [package reference](https://docs.microsoft.com/en-us/nuget/consume-packages/package-references-in-project-files) in the `*.csproj` file under the `PackageReference` node.

   ```xml
   <ItemGroup>
       <!-- ... -->
       <PackageReference Include="Contoso.Utility.UsefulStuff" Version="3.6.0" />
       <!-- ... -->
   </ItemGroup>
   ```

2. Create a [NuGet.Config](https://docs.microsoft.com/en-us/nuget/reference/nuget-config-file) file in the project folder.
     * Use the `packageSources` section to reference your NuGet feed location. Important: The NuGet feed must be publicly accessible.
     * Use the `packageSourceCredentials` section to configure username and password credentials. 

   ```xml
   <packageSources>
       <add key="Contoso" value="https://contoso.com/packages/" />
   </packageSources>

   <packageSourceCredentials>
       <Contoso>
           <add key="Username" value="user@contoso.com" />
           <add key="ClearTextPassword" value="33f!!lloppa" />
       </Contoso>
   </packageSourceCredentials>
   ```

3. If you're using source code control:
    - Reference `NuGet.Config` in your `.gitignore` file so you don't accidentally commit credentials to your source repository.
    - Open the `vsce.yaml` file in your project, and locate the `build` section, and insert the following snippet to ensure that the `NuGet.Config` file will be synced to Azure so that it used during the container image build process. (By default, Connected Environment does not synchronize files that match `.gitignore` and `.dockerignore` rules.)

        ```yaml
        build:
        useGitIgnore: true
        ignore:
        - “!NuGet.Config”
        ```


## Next steps

Once you have completed the above steps, the next time you run `vsce up` (or hit `F5` in VSCode or Visual Studio), Connected Environment will synchronize the `NuGet.Config` file to Azure, which is then utilized by `dotnet restore` to install package dependencies in the container.


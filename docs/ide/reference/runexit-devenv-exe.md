---
title: "-Runexit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.technology: 
  - "vs-ide-general"
ms.topic: "conceptual"
helpviewer_keywords: 
  - "runexit Devenv switch"
  - "Devenv, /runexit switch"
  - "/runexit Devenv switch"
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: "gewarren"
ms.author: "gewarren"
manager: douge
ms.workload: 
  - "multiple"
---
# /Runexit (devenv.exe)
Compiles and runs the specified project or solution, and then closes the integrated development environment (IDE).  
  
## Syntax  
  
```  
devenv /runexit {SolutionName|ProjectName}  
```  
  
## Arguments  
 `SolutionName`  
 Required. The full path and name of a solution file.  
  
 `ProjectName`  
 Required. The full path and name of a project file.  
  
## Remarks  
 Compiles and runs the specified project or solution according to the settings specified for the active solution configuration. This switch minimizes the IDE while the project or solution is run, and it closes the IDE after the project or solution has completed running.  
  
-   Enclose strings that include spaces in double quotation marks.  
  
-   Summary information, including errors, can be displayed in the **Command** window, or in any log file specified with the `/out` switch.  
  
## Example  
 This example runs the solution `MySolution` in a minimized IDE using the active deployment configuration, and then closes the IDE.  
  
```  
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"  
```  
  
## See Also  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
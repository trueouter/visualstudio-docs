---
title: "IDiaEnumFrameData::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.technology: 
  - "vs-ide-debug"
ms.topic: "conceptual"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumFrameData::Clone Method"
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: "mikejo5000"
ms.author: "mikejo"
manager: douge
ms.workload: 
  - "multiple"
---
# IDiaEnumFrameData::Clone
Creates an enumerator that contains the same enumeration state as the current enumerator.  
  
## Syntax  
  
```C++  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### Parameters  
 ppenum  
 [out] Returns an [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) object that contains a duplicate  of the enumerator. The frame data is not duplicated, only the enumerator.  
  
## Return Value  
 If successful, returns `S_OK`; otherwise, returns an error code.  
  
## See Also  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
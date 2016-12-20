---
title: "GetExportPragmas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetExportPragmas"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetExportPragmas 方法"
ms.assetid: ef21f6a3-d83f-4e19-9323-ca28cc40c8fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetExportPragmas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

加入 pragma 以匯出函式。  
  
## 語法  
  
```  
  
function GetExportPragmas( );  
  
```  
  
## 傳回值  
 包含匯出 pragma 的字串，  可以是下列其中一項：  
  
-   `#pragma comment(linker, "/EXPORT:DllCanUnloadNow=_DllCanUnloadNow@0,PRIVATE")'`  
  
-   `#pragma comment(linker, "/EXPORT:DllGetClassObject=_DllGetClassObject@12,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllRegisterServer=_DllRegisterServer@0,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllUnregisterServer=_DllUnregisterServer@0,PRIVATE")`  
  
## 備註  
 呼叫此函式以加入用於匯出函式的 pragma。  
  
## 範例  
  
```  
oDllCanUnloadNow.StartPoint.Insert(GetExportPragmas() + "\r\n");  
oCM.Synchronize();  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [註解](../preprocessor/comment-c-cpp.md)
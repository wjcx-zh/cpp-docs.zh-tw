---
title: "GetUniqueFileName | Microsoft Docs"
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
  - "GetUniqueFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUniqueFilename 方法"
ms.assetid: f9760e1a-82d0-4d8b-b00a-6f4c36f6b2c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetUniqueFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

傳回唯一的檔名。  
  
## 語法  
  
```  
  
      function GetUniqueFileName(   
   strDirectory,   
   strFileName    
);  
```  
  
#### 參數  
 *strDirectory*  
 用來搜尋檔名的目錄  
  
 `strFileName`  
 要檢查的檔名。  
  
## 傳回值  
 如果檔名是唯一的，則會在 `strFileName` 中指出，否則這個函式會傳回 `strFileName`，並在其後附加 1 到 9999999 中的一個數字，使它成為唯一的名稱。  如果未提供 `strFileName`，則這個函式會使用 [GetTempName 方法](jsmthGetTempName)傳回唯一的檔名。  
  
## 備註  
 傳回唯一的檔名。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetProjectFile](../ide/getprojectfile.md)
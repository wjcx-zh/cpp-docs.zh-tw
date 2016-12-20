---
title: "IncludeCodeElementDeclaration | Microsoft Docs"
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
  - "IncludeCodeElementDeclaration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncludeCodeElementDeclaration 方法"
ms.assetid: 714e76e4-76bc-439a-982a-cf9d4ada7677
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IncludeCodeElementDeclaration
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果在 `oProj` 中找得到此標頭的話，則將包含實作 `strCodeElemName` 標頭的 Include 陳述式加入至 `strInFile`。  
  
## 語法  
  
```  
  
      function IncludeCodeElementDeclaration(   
   oProj,   
   strCodeElemName,   
   strInFile    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
 `strCodeElemName`  
 要在定義標頭中搜尋之程式碼項目的完整名稱。  
  
 `strInFile`  
 包含此定義標頭的檔案 \(如果找得到的話\)。  
  
## 備註  
 如果在 `oProj` 中找得到此標頭的話，則將包含實作 `strCodeElemName` 標頭的 Include 陳述式加入至 `strInFile`。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
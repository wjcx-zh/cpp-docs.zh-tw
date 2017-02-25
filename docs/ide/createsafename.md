---
title: "CreateSafeName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateSafeName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateSafeName 方法"
ms.assetid: 3a0dd4af-776d-4c25-aff9-4c539f173cb8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CreateSafeName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

產生 C\+\+ 易記名稱。  
  
## 語法  
  
```  
  
      function CreateSafeName(   
   strName    
);  
```  
  
#### 參數  
 `strName`  
 舊名稱。  
  
## 傳回值  
 新的、安全的名稱。  
  
## 備註  
 若一個名稱包含 C\+\+ 無法使用的字元，請呼叫此函式來建立 C\+\+ 易記名稱。  C\+\+ 可接受的名稱包括大小寫字母、數字或底線 \("\_"\)。  
  
 此函式會逐一字元地檢查舊名稱，並會略過任何不能使用的字元。  如果舊名稱未包含易記字元，則此函式會以「My」做為新名稱來傳回。  如果新的易記名稱以數字開始，則此函式會在新名稱前面附加「My」。  
  
## 範例  
  
```  
// Get the project name  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Set the project name to the safe project name.   
var strSafeProjectName = CreateSafeName(strProjectName);  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
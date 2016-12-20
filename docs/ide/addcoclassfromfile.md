---
title: "AddCoclassFromFile | Microsoft Docs"
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
  - "AddCoclassFromFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddCoclassFromFile 方法"
ms.assetid: a8a211fd-2df3-4361-8137-9c0d999b7f88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddCoclassFromFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將包含 coclass 的樣板檔轉譯並插入至專案的 .idl 檔中。  
  
## 語法  
  
```  
  
      function AddCoclassFromFile(   
   oCM,   
   strCoclassFile    
);  
```  
  
#### 參數  
 `oCM`  
 [Visual C\+\+ Code Model](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b) 物件。  
  
 *strCoclassFile*  
 樣板檔名稱，不包含路徑。  
  
## 備註  
 呼叫此函式將包含 Coclass 的樣板檔轉譯並插入至專案的 .idl 檔中。  
  
## 範例  
  
```  
// Render myproj.idl and insert into the project's .idl.  
AddCoclassFromFile(oCM, "myproj.idl");  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
---
title: "AddInterfaceFromFile | Microsoft Docs"
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
  - "AddInterfaceFromFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddInterfaceFromFile 方法"
ms.assetid: fa848690-ad98-4fb4-bbcf-dffcaad05df2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddInterfaceFromFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

轉譯並插入包含介面的樣板檔。  
  
## 語法  
  
```  
  
      function AddInterfaceFromFile(   
   oCM,   
   strInterfaceFile    
);  
```  
  
#### 參數  
 `oCM`  
 [Visual C\+\+ Code Model](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b) 物件。  
  
 *strInterfaceFile*  
 僅含樣板檔名稱，不包含路徑。  
  
## 備註  
 呼叫此函式將包含介面的樣板檔轉譯並插入至專案的 .idl 檔中。  
  
 如果加入介面沒有成功，則函式會顯示錯誤訊息。  
  
## 範例  
  
```  
// Render myint.idl and insert into strProject.idl  
AddInterfaceFromFile(oCM, "myint.idl");  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)
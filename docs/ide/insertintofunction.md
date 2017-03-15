---
title: "InsertIntoFunction | Microsoft Docs"
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
  - "InsertIntoFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InsertIntoFunction 方法"
ms.assetid: 50500c3c-bee3-4a9c-a403-7dcd752de23c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InsertIntoFunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [AddATLSupportToProject](../ide/addatlsupporttoproject.md) 所使用來將程式碼插入至 [InitInstance](../Topic/CWinApp::InitInstance.md)。  
  
## 語法  
  
```  
  
      function InsertIntoFunction(   
   oFunction,   
   strSearchString,   
   nStartLine,   
   nEndLine,   
   bInsideIfBlock    
);  
```  
  
#### 參數  
 *oFunction*  
 將進行插入動作的函式物件。  
  
 `strSearchString`  
 搜尋用來判斷插入點的字串。  
  
 *nStartLine*  
 要傳遞給 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md) 的起始行。  
  
 *nEndLine*  
 要傳遞給 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md) 的結束行。  
  
 *bInsideIfBlock*  
 指示是否要插入至函式區塊內。  
  
## 傳回值  
 如果成功則為 **True**，否則為 **False**。  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [GetMemberfunction](../ide/getmemberfunction.md)
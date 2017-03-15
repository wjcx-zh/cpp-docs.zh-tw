---
title: "IsMFCProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IsMFCProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsMFCProject 方法"
ms.assetid: 98dd57df-9fdb-40d7-afcf-4b99e9d54dad
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# IsMFCProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

檢查專案是否為 MFC 架構。  
  
## 語法  
  
```  
  
      function IsMFCProject(   
   oProj,   
   bCWinAppRequired    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
 *bCWinAppRequired*  
 表示此次檢查是否包括擴充 DLL。  
  
## 傳回值  
 如果專案是 MFC 專案則為 **true**，否則為 **false**。  
  
## 備註  
 使用此函式來判斷所選的專案是否為 MFC 專案。  
  
## 範例  
  
```  
if (!IsMFCProject(selProj, true))  
   {  
      if (gbExceptionThrown)  
         return false;  
      var L_ErrMsg2_Text = "ATL support can only be added to MFC EXEs or MFC Regular DLLs.";  
      wizard.ReportError(L_ErrMsg2_Text);  
      return false;  
   }  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [IsATLProject](../ide/isatlproject.md)   
 [IsAttributedProject](../ide/isattributedproject.md)
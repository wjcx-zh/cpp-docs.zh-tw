---
title: "CanAddMFCClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanAddMFCClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddMFCClass 方法"
ms.assetid: 6a97a410-b028-4aad-9b06-04c12cf481eb
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CanAddMFCClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由精靈所呼叫，用來驗證使用者是否能夠將 MFC 類別加入至專案的函式中。  
  
## 語法  
  
```  
  
      function CanAddMFCClass(   
   oProj,   
   oObject    
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
 `oObject`  
 選取的物件。  此處是指目前的專案。  
  
## 傳回值  
 如果可以加入類別則為 **True**；如果使用者於非 MFC 且缺乏 MFC 支援的專案呼叫此函式則為 **False**。  
  
## 備註  
 由精靈所呼叫的函式，用來驗證專案與將要執行的程式碼精靈是否相容 \(也就是說，它可以接受 MFC 類別\)。  
  
 當 PREPROCESS\_FUNCTION 參數位於[專案控制項的 .vsz 檔內](../ide/dot-vsz-file-project-control.md)時，精靈會呼叫這個函式，並檢查 [Visual C\+\+ 程式碼模型](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)物件是否可用。  如果無法使用此程式碼模型，則函式將報告錯誤並傳回 **false**。  
  
## 範例  
  
```  
// Determine if an MFC class can be added to the project  
if (CanAddMFCClass(selProj, selObj))  
{  
   return true;  
}  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [C\+\+ 精靈的 JScript 函式](../ide/jscript-functions-for-cpp-wizards.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [CanAddClass](../ide/canaddclass.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)
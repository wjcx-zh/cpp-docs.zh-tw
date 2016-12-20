---
title: "CanAddATLClass | Microsoft Docs"
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
  - "CanAddATLClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddATLClass 方法"
ms.assetid: 7a8abf90-c1b8-475c-af22-7948478084f9
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanAddATLClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此由精靈所呼叫，用來驗證使用者是否能將 ATL 類別加入至專案中。  
  
## 語法  
  
```  
  
      function CanAddATLClass(   
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
 如果可以加入類別則為 **True**；如果使用者於非 ATL 且缺乏 ATL 支援的專案呼叫此函式則為 **False**。  
  
## 備註  
 由精靈所呼叫的函式，用來驗證專案是否與將要執行的程式碼精靈相容 \(換句話說，它可以接受 ATL 類別\)。  
  
 當 PREPROCESS\_FUNCTION 參數位於[專案控制項的 .vsz 檔內](../ide/dot-vsz-file-project-control.md)時，精靈會呼叫這個函式，並檢查 [Visual C\+\+ 程式碼模型](http://msdn.microsoft.com/zh-tw/dd6452c2-1054-44a1-b0eb-639a94a1216b)是否可用。  如果無法使用此程式碼模型，則函式將報告錯誤並傳回 **false**。  
  
## 範例  
  
```  
// Determine if an ATL class can be added to the project  
if (CanAddATLClass(selProj, selObj))  
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
 [IsMFCProject](../ide/ismfcproject.md)   
 [CanAddMFCClass](../ide/canaddmfcclass.md)
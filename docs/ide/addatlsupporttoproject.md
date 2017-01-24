---
title: "AddATLSupportToProject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddATLSupportToProject 方法"
ms.assetid: 26708f22-1e9b-4432-83b2-ed94c765b753
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddATLSupportToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

將 ATL 支援加入至 MFC 專案中。  
  
## 語法  
  
```  
  
      function AddATLSupportToProject(   
   oProj   
);  
```  
  
#### 參數  
 `oProj`  
 選取的專案。  
  
## 傳回值  
 成功地將 ATL 支援加入至 MFC 專案時為 **True**。  
  
## 備註  
 使用這個函式將 ATL 支援加入至由精靈所建立的 MFC 專案中。  
  
 精靈會顯示一個訊息方塊來確認是否要將 ATL 支援加入至 MFC 專案中。  在進行確認時，精靈會檢查現有的支援，並且加入所有需要的 GUID、樣板、標頭和額外的功能，以便由精靈所建立的 MFC 專案能夠支援 ATL。  
  
## 範例  
  
```  
var oCM = selProj.CodeModel;  
var L_TRANSACTION_Text = "Add ATL Support To Project";  
oCM.StartTransaction(L_TRANSACTION_Text);  
var bRet = AddATLSupportToProject(selProj);  
if (bRet)  
   oCM.CommitTransaction();  
else  
   oCM.AbortTransaction();  
return bRet;  
```  
  
## 請參閱  
 [使用 Common JScript 函式自訂 C\+\+ 精靈](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [建立自訂精靈](../ide/creating-a-custom-wizard.md)   
 [設計精靈](../ide/designing-a-wizard.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)   
 [ATL 簡介](../atl/introduction-to-atl.md)
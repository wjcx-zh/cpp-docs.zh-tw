---
title: "關閉對話方塊 | Microsoft Docs"
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
  - "對話方塊, 關閉"
  - "MFC 對話方塊, 關閉"
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 關閉對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者選取其按鈕，通常會確定按鈕或取消按鈕之一，強制回應對話方塊關閉。  選擇確定或取消按鈕原因視窗傳送對話方塊會與按鈕的 ID 的 **BN\_CLICKED** 控制通知訊息， **IDOK** 或 **IDCANCEL**。  `CDialog` 為這些訊息的預設處理函式: `OnOK` 和 `OnCancel`。  預設處理常式呼叫 `EndDialog` 成員函式關閉對話方塊視窗。  您也可以從自己的程式碼呼叫 `EndDialog` 。  如需詳細資訊，請參閱類別 `CDialog` 的 [EndDialog](../Topic/CDialog::EndDialog.md) 成員函式於 *MFC 參考*。  
  
 已關閉和刪除非強制回應對話方塊，覆寫 `PostNcDestroy` 和叫用 **this** 指標的 **delete** 運算子。  [終結對話方塊](../mfc/destroying-the-dialog-box.md) 說明會發生何種情況下。  
  
## 請參閱  
 [對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)
---
title: "處理索引標籤控制項通知訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CTabCtrl 類別, 處理通知"
  - "告知, CTabCtrl 中的處理"
  - "告知, 索引標籤控制項"
  - "處理通知"
  - "索引標籤控制項, 處理通知"
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理索引標籤控制項通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者按一下選項或按鈕，索引標籤控制項 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\) 傳送通知訊息至其父視窗。  如果您想要執行某個動作以回應，請處理這些訊息。  例如，在中，當使用者按一下索引標籤時，您可能想要在顯示之前預先設定網頁上的控制項資料。  
  
 從索引標籤控制項處理 **WM\_NOTIFY** 訊息中的檢視或對話方塊類別。  使用屬性視窗建立視通知訊息的 switch 的 [OnChildNotify](../Topic/CWnd::OnChildNotify.md) 處理常式函式被處理。  如需選項控制項傳送給其父視窗通知的清單，請參閱 [索引標籤控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb760548) 的 **Notifications** 部分以 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]為單位\)。  
  
## 請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)
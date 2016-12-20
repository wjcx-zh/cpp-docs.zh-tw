---
title: "處理清單控制項中的通知訊息 | Microsoft Docs"
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
  - "CListCtrl 類別, 處理通知"
  - "處理通知"
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 處理清單控制項中的通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用者按一下資料行行首，請拖曳圖示，編輯標籤，依此類推，清單控制項 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 傳送通知訊息至其父視窗。  如果您想要執行某個動作以回應，請處理這些訊息。  例如，當使用者按一下資料行行首時，您可能會想要排序依據按一下資料行的內容項目，在 Microsoft Outlook。  
  
 從清單控制項處理 **WM\_NOTIFY** 訊息中的檢視或對話方塊類別。  使用屬性視窗建立視通知訊息的 switch 的 [OnChildNotify](../Topic/CWnd::OnChildNotify.md) 處理常式函式被處理。  
  
 如需清單控制項可以傳送給其父視窗通知的清單，請參閱 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [清單檢視控制項參考。](http://msdn.microsoft.com/library/windows/desktop/bb774737) 。  
  
## 請參閱  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控制項](../mfc/controls-mfc.md)
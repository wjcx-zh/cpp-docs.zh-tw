---
title: "處理工具提示的 TTN_NEEDTEXT 告知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TTN_NEEDTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "告知, 工具提示"
  - "工具提示 [C++], 告知"
  - "TTN_NEEDTEXT 訊息"
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 處理工具提示的 TTN_NEEDTEXT 告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

做為 [啟用工具提示](../mfc/enabling-tool-tips.md)一節中，您可以將下列輸入處理 **TTN\_NEEDTEXT** 訊息至主控視窗的訊息對應:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]  
  
 `memberFxn`  
 要呼叫的，當文字此按鈕所需的成員函式。  
  
 請注意工具提示的識別碼一定是 0。  
  
 宣告在類別定義的處理常式函式:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_2.h)]  
  
 其中斜體參數:  
  
 `id`  
 傳送通知控制項的識別項。  不適用。  控制項 ID 從 **NMHDR** 結構中取得。  
  
 `pNMHDR`  
 out [NMTTDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb760258) 結構的指標。  這個結構進一步在 [TOOLTIPTEXT 結構](../mfc/tooltiptext-structure.md)也會討論。  
  
 `pResult`  
 產生的指標可以設定的程式碼，在返回之前。  **TTN\_NEEDTEXT** 處理常式可以忽略 `pResult` 參數。  
  
 例如表單檢視告知處理常式:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]  
  
 呼叫 `EnableToolTips` \(從 `OnInitDialog`取得的片段\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/CPP/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]  
  
## 請參閱  
 [非衍生自 CFrameWnd 之視窗中的工具提示](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
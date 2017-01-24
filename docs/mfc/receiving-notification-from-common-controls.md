---
title: "從通用控制項接收告知 | Microsoft Docs"
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
  - "ON_NOTIFY"
  - "WM_NOTIFY"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通用控制項 [C++], 告知"
  - "控制項 [MFC], 告知"
  - "告知, 通用控制項"
  - "ON_NOTIFY 巨集"
  - "OnNotify 方法"
  - "從通用控制項接收告知"
  - "Windows 通用控制項 [C++], 告知"
  - "WM_NOTIFY 訊息"
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 從通用控制項接收告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通用控制項會傳送通知訊息至父視窗的子視窗，當事件，例如來自使用者的輸入，在控制項時發生。  
  
 應用程式依賴這些通知訊息判斷行動使用者要採用。  最常見的控制項傳送通知訊息在 **WM\_NOTIFY** 訊息。  視窗控制項傳送大部分通知訊息在 **WM\_COMMAND** 訊息。  [CWnd::OnNotify](../Topic/CWnd::OnNotify.md) 是 **WM\_NOTIFY** 訊息的處理常式。  使用 `CWnd::OnCommand`， `OnNotify` 的實作會告知訊息處理的 `OnCmdMsg` 在訊息對應。  處理的通知訊息對應項目是 `ON_NOTIFY`。  如需詳細資訊，請參閱 [Technical Note 61:ON\_NOTIFY 和 WM\_NOTIFY 訊息](../mfc/tn061-on-notify-and-wm-notify-messages.md)。  
  
 此外，衍生類別可以處理它的通知訊息使用訊息反映」。如需詳細資訊，請參閱 [Technical Note 62:視窗的訊息反映](../mfc/tn062-message-reflection-for-windows-controls.md)。  
  
## 擷取通知訊息的游標位置  
 在某些情況下，當某些通知訊息由通用控制項時，接收決定游標的目前位置會很有用。  例如，在中，當通用控制項收到 **NM\_RCLICK** 通知訊息時，判斷目前游標位置很有用。  
  
 有一種簡單的方式是透過呼叫 `CWnd::GetCurrentMessage`來完成。  不過，在這種情況下，傳送訊息時，這個方法只會擷取游標位置。  因為資料指標可能移動，因為傳送您必須呼叫 **CWnd::GetCursorPos** 取得目前游標位置。  
  
> [!NOTE]
>  應該 在訊息處理常式內只呼叫`CWnd::GetCurrentMessage` 。  
  
 將下列程式碼加入至告知訊息的訊息處理常式的主體 \(在本例中， **NM\_RCLICK**\):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/CPP/receiving-notification-from-common-controls_1.cpp)]  
  
 此時，滑鼠游標位置在 `cursorPos` 物件中。  
  
## 請參閱  
 [建立及使用控制項](../mfc/making-and-using-controls.md)   
 [控制項](../mfc/controls-mfc.md)
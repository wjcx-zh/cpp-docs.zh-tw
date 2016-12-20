---
title: "WM_ 訊息：T - Z | Microsoft Docs"
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
  - "ON_WM_TCARD"
  - "ON_WM_WININICHANGE"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_VSCROLL"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_WINDOWPOSCHANGING"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_TCARD"
  - "ON_WM_TIMECHANGE"
  - "ON_WM_TIMER"
  - "ON_WM_VKEYTOITEM"
  - "ON_WM_VSCROLL"
  - "ON_WM_VSCROLLCLIPBOARD"
  - "ON_WM_WINDOWPOSCHANGED"
  - "ON_WM_WINDOWPOSCHANGING"
  - "ON_WM_WININICHANGE"
  - "WM_ 訊息"
ms.assetid: c528bb2e-ddb5-4da6-b652-432a387408b8
caps.latest.revision: 16
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WM_ 訊息：T - Z
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型:  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_WM\_TCARD \(\)|afx\_msg 空 [OnTCard](../Topic/CWnd::OnTCard.md)\(UINT， DWORD\);|  
|ON\_WM\_TIMECHANGE \(\)|afx\_msg 空 [OnTimeChange](../Topic/CWnd::OnTimeChange.md)\(\);|  
|ON\_WM\_TIMER \(\)|afx\_msg 空 [OnTimer](../Topic/CWnd::OnTimer.md)\(inUINT\_PTR\);|  
|ON\_WM\_UNICHAR \(\)|afx\_msg 空 [OnUniChar](../Topic/CWnd::OnUniChar.md)\(、、、，、\);|  
|ON\_WM\_UNINITMENUPOPUP \(\)|afx\_msg 空 [OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)\(CMenu\*， UINT\);|  
|ON\_WM\_USERCHANGED \(\)|afx\_msg 空 [OnUserChanged](../Topic/CWnd::OnUserChanged.md)\(\);|  
|ON\_WM\_VKEYTOITEM \(\)|afx\_msg int [OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)\(UINT， CWnd\*， UINT\);|  
|ON\_WM\_VSCROLL \(\)|afx\_msg 空 [OnVScroll](../Topic/CWnd::OnVScroll.md)\(、，、， CWnd\*\);|  
|ON\_WM\_VSCROLLCLIPBOARD \(\)|afx\_msg 空 [OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)\(CWnd\*，、，、\);|  
|ON\_WM\_WINDOWPOSCHANGED \(\)|afx\_msg 空 [OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)\(WINDOWPOS\*\);|  
|ON\_WM\_WINDOWPOSCHANGING \(\)|afx\_msg 空 [OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)\(WINDOWPOS\*\);|  
|ON\_WM\_WININICHANGE \(\)|afx\_msg 空 [OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)\(或\);|  
|ON\_WM\_WTSSESSION\_CHANGE \(\)|afx\_msg 空 [OnSessionChange](../Topic/CWnd::OnSessionChange.md)\(、，、\);|  
|ON\_WM\_XBUTTONDBLCLK \(\)|afx\_msg 空 [OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)\(、，、， CPoint\);|  
|ON\_WM\_XBUTTONDOWN \(\)|afx\_msg 空 [OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)\(、，、， CPoint\);|  
|ON\_WM\_XBUTTONUP \(\)|afx\_msg 空 [OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)\(、，、， CPoint\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)
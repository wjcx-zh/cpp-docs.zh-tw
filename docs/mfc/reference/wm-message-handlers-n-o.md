---
title: "WM_ 訊息處理常式：N - O | Microsoft Docs"
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
  - "ON_WM_NCHITTEST"
  - "ON_WM_NCLBUTTONDOWN"
  - "ON_WM_NCCALCSIZE"
  - "ON_WM_NCLBUTTONUP"
  - "ON_WM_NCPAINT"
  - "ON_WM_NCMBUTTONUP"
  - "ON_WM_NCCREATE"
  - "ON_WM_NCACTIVATE"
  - "ON_WM_NCMOUSEMOVE"
  - "ON_WM_NCRBUTTONDBLCLK"
  - "ON_WM_NCLBUTTONDBLCLK"
  - "ON_WM_NCDESTROY"
  - "ON_WM_NCMBUTTONDBLCLK"
  - "ON_WM_NCRBUTTONDOWN"
  - "ON_WM_NCRBUTTONUP"
  - "ON_WM_NCMBUTTONDOWN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_NCACTIVATE"
  - "ON_WM_NCCALCSIZE"
  - "ON_WM_NCCREATE"
  - "ON_WM_NCDESTROY"
  - "ON_WM_NCHITTEST"
  - "ON_WM_NCLBUTTONDBLCLK"
  - "ON_WM_NCLBUTTONDOWN"
  - "ON_WM_NCLBUTTONUP"
  - "ON_WM_NCMBUTTONDBLCLK"
  - "ON_WM_NCMBUTTONDOWN"
  - "ON_WM_NCMBUTTONUP"
  - "ON_WM_NCMOUSEMOVE"
  - "ON_WM_NCPAINT"
  - "ON_WM_NCRBUTTONDBLCLK"
  - "ON_WM_NCRBUTTONDOWN"
  - "ON_WM_NCRBUTTONUP"
  - "WM_ 訊息"
ms.assetid: 4efd1cda-b642-4e8b-89e8-73255fa70d77
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WM_ 訊息處理常式：N - O
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在左邊的下列對應項目對應於右邊的函式原型：  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_WM\_NCACTIVATE\(\)|afx\_msg BOOL [OnNcActivate](../Topic/CWnd::OnNcActivate.md)\(BOOL\);|  
|ON\_WM\_NCCALCSIZE\(\)|afx\_msg 空 [OnNcCalcSize](../Topic/CWnd::OnNcCalcSize.md)\(BOOL， NCCALCSIZE\_PARAMS FAR\*\);|  
|ON\_WM\_NCCREATE\(\)|afx\_msg BOOL [OnNcCreate](../Topic/CWnd::OnNcCreate.md)\(LPCREATESTRUCT\);|  
|ON\_WM\_NCDESTROY\(\)|afx\_msg void [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)\(\);|  
|ON\_WM\_NCHITTEST\(\)|afx\_msg LRESULT [OnNcHitTest](../Topic/CWnd::OnNcHitTest.md)\(CPoint\);|  
|ON\_WM\_NCLBUTTONDBLCLK\(\)|afx\_msg void [OnNcLButtonDblClk](../Topic/CWnd::OnNcLButtonDblClk.md)\(UINT， CPoint\);|  
|ON\_WM\_NCLBUTTONDOWN\(\)|afx\_msg void [OnNcLButtonDown](../Topic/CWnd::OnNcLButtonDown.md)\(UINT， CPoint\);|  
|ON\_WM\_NCLBUTTONUP\(\)|afx\_msg void [OnNcLButtonUp](../Topic/CWnd::OnNcLButtonUp.md)\(UINT， CPoint\);|  
|ON\_WM\_NCMBUTTONDBLCLK\(\)|afx\_msg void [OnNcMButtonDblClk](../Topic/CWnd::OnNcMButtonDblClk.md)\(UINT, CPoint\);|  
|ON\_WM\_NCMBUTTONDOWN\(\)|afx\_msg void [OnNcMButtonDown](../Topic/CWnd::OnNcMButtonDown.md)\(UINT, CPoint\);|  
|ON\_WM\_NCMBUTTONUP\(\)|afx\_msg void [OnNcMButtonUp](../Topic/CWnd::OnNcMButtonUp.md)\(UINT, CPoint\);|  
|ON\_WM\_NCMOUSEHOVER\(\)|afx\_msg void [OnNcMouseHover](../Topic/CWnd::OnNcMouseHover.md)\(UINT, CPoint\);|  
|ON\_WM\_NCMOUSELEAVE\(\)|afx\_msg void [OnNcMouseLeave](../Topic/CWnd::OnNcMouseLeave.md)\(\);|  
|ON\_WM\_NCMOUSEMOVE\(\)|afx\_msg void [OnNcMouseMove](../Topic/CWnd::OnNcMouseMove.md)\(UINT, CPoint\);|  
|ON\_WM\_NCPAINT\(\)|afx\_msg void [OnNcPaint](../Topic/CWnd::OnNcPaint.md)\(\);|  
|ON\_WM\_NCRBUTTONDBLCLK\(\)|afx\_msg void [OnNcRButtonDblClk](../Topic/CWnd::OnNcRButtonDblClk.md)\(UINT, CPoint\);|  
|ON\_WM\_NCRBUTTONDOWN\(\)|afx\_msg void [OnNcRButtonDown](../Topic/CWnd::OnNcRButtonDown.md)\(UINT, CPoint\);|  
|ON\_WM\_NCRBUTTONUP\(\)|afx\_msg void [OnNcRButtonUp](../Topic/CWnd::OnNcRButtonUp.md)\(UINT, CPoint\);|  
|ON\_WM\_NCXBUTTONDBLCLK\(\)|void [OnNcXButtonDblClk](../Topic/CWnd::OnNcXButtonDblClk.md)\(short, UINT, CPoint\);|  
|ON\_WM\_NCXBUTTONDOWN\(\)|afx\_msg void [OnNcXButtonDown](../Topic/CWnd::OnNcXButtonDown.md)\(short, UINT, CPoint\);|  
|ON\_WM\_NCXBUTTONUP\(\)|afx\_msg void [OnNcXButtonUp](../Topic/CWnd::OnNcXButtonUp.md)\(short, UINT, CPoint\);|  
|ON\_WM\_NEXTMENU\(\)|afx\_msg void [OnNextMenu](../Topic/CWnd::OnNextMenu.md)\(UINT, LPMDINEXTMENU\);|  
|ON\_WM\_NOTIFYFORMAT\(\)|afx\_msg UINT [OnNotifyFormat](../Topic/CWnd::OnNotifyFormat.md)\(CWnd\*, UINT\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)
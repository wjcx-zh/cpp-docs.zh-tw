---
title: "WM_ 訊息：P - R | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_RBUTTONUP"
  - "ON_WM_PALETTECHANGED"
  - "ON_WM_RBUTTONDBLCLK"
  - "ON_WM_QUERYENDSESSION"
  - "ON_WM_PARENTNOTIFY"
  - "ON_WM_PALETTEISCHANGING"
  - "ON_WM_QUERYOPEN"
  - "ON_WM_PAINT"
  - "ON_WM_QUERYNEWPALETTE"
  - "ON_WM_RBUTTONDOWN"
  - "ON_WM_RENDERALLFORMATS"
  - "ON_WM_PAINTCLIPBOARD"
  - "ON_WM_RENDERFORMAT"
  - "ON_WM_QUERYDRAGICON"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_PAINT"
  - "ON_WM_PAINTCLIPBOARD"
  - "ON_WM_PALETTECHANGED"
  - "ON_WM_PALETTEISCHANGING"
  - "ON_WM_PARENTNOTIFY"
  - "ON_WM_QUERYDRAGICON"
  - "ON_WM_QUERYENDSESSION"
  - "ON_WM_QUERYNEWPALETTE"
  - "ON_WM_QUERYOPEN"
  - "ON_WM_RBUTTONDBLCLK"
  - "ON_WM_RBUTTONDOWN"
  - "ON_WM_RBUTTONUP"
  - "ON_WM_RENDERALLFORMATS"
  - "ON_WM_RENDERFORMAT"
  - "WM_ 訊息"
ms.assetid: f46962e5-8329-4f1f-9b4d-fdad2a5ce1f8
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# WM_ 訊息：P - R
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型:  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_WM\_PAINT \(\)|afx\_msg 空 [OnPaint](../Topic/CWnd::OnPaint.md)\(\);|  
|ON\_WM\_PAINTCLIPBOARD \(\)|afx\_msg 空 [OnPaintClipboard](../Topic/CWnd::OnPaintClipboard.md)\(CWnd\*，控制代碼\);|  
|ON\_WM\_PALETTECHANGED \(\)|afx\_msg 空 [OnPaletteChanged](../Topic/CWnd::OnPaletteChanged.md)\(CWnd\*\);|  
|ON\_WM\_PALETTEISCHANGING \(\)|afx\_msg 空 [OnPaletteIsChanging](../Topic/CWnd::OnPaletteIsChanging.md)\(CWnd\*\);|  
|ON\_WM\_PARENTNOTIFY \(\)|afx\_msg 空 [OnParentNotify](../Topic/CWnd::OnParentNotify.md)\(UINT， long\);|  
|ON\_WM\_POWERBROADCAST \(\)|afx\_msg、 [OnPowerBroadcast](../Topic/CWnd::OnPowerBroadcast.md)\(、，、\);|  
|ON\_WM\_QUERYDRAGICON \(\)|afx\_msg HCURSOR [OnQueryDragIcon](../Topic/CWnd::OnQueryDragIcon.md)\(\)、\(\);|  
|ON\_WM\_QUERYENDSESSION \(\)|afx\_msg BOOL [OnQueryEndSession](../Topic/CWnd::OnQueryEndSession.md)\(\)、\(\);|  
|ON\_WM\_QUERYNEWPALETTE \(\)|afx\_msg BOOL [OnQueryNewPalette](../Topic/CWnd::OnQueryNewPalette.md)\(\)、\(\);|  
|ON\_WM\_QUERYOPEN \(\)|afx\_msg BOOL [OnQueryOpen](../Topic/CWnd::OnQueryOpen.md)\(\)、\(\);|  
|ON\_WM\_RBUTTONDBLCLK \(\)|afx\_msg 空 [OnRButtonDblClk](../Topic/CWnd::OnRButtonDblClk.md)\(UINT， CPoint\);|  
|ON\_WM\_RBUTTONDOWN \(\)|afx\_msg 空 [OnRButtonDown](../Topic/CWnd::OnRButtonDown.md)\(UINT， CPoint\);|  
|ON\_WM\_RBUTTONUP \(\)|afx\_msg 空 [OnRButtonUp](../Topic/CWnd::OnRButtonUp.md)\(UINT， CPoint\);|  
|ON\_WM\_RENDERALLFORMATS \(\)|afx\_msg 空 [OnRenderAllFormats](../Topic/CWnd::OnRenderAllFormats.md)\(\);|  
|ON\_WM\_RENDERFORMAT \(\)|afx\_msg 空 [OnRenderFormat](../Topic/CWnd::OnRenderFormat.md)\(、\);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)
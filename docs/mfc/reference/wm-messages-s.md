---
title: "WM_ 訊息：S | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_SYSDEADCHAR"
  - "ON_WM_SYSKEYDOWN"
  - "ON_WM_STYLECHANGING"
  - "ON_WM_STYLECHANGED"
  - "ON_WM_SPOOLERSTATUS"
  - "ON_WM_SYSCHAR"
  - "ON_WM_SETFOCUS"
  - "ON_WM_SIZE"
  - "ON_WM_SIZING"
  - "ON_WM_SETCURSOR"
  - "ON_WM_SYSCOMMAND"
  - "ON_WM_SETTINGCHANGE"
  - "ON_WM_SHOWWINDOW"
  - "ON_WM_SYSKEYUP"
  - "ON_WM_SIZECLIPBOARD"
  - "ON_WM_SYSCOLORCHANGE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_SETCURSOR"
  - "ON_WM_SETFOCUS"
  - "ON_WM_SETTINGCHANGE"
  - "ON_WM_SHOWWINDOW"
  - "ON_WM_SIZE"
  - "ON_WM_SIZECLIPBOARD"
  - "ON_WM_SIZING"
  - "ON_WM_SPOOLERSTATUS"
  - "ON_WM_STYLECHANGED"
  - "ON_WM_STYLECHANGING"
  - "ON_WM_SYSCHAR"
  - "ON_WM_SYSCOLORCHANGE"
  - "ON_WM_SYSCOMMAND"
  - "ON_WM_SYSDEADCHAR"
  - "ON_WM_SYSKEYDOWN"
  - "ON_WM_SYSKEYUP"
  - "WM_ 訊息"
ms.assetid: 4b9aec79-a98f-4aa0-a3d9-110941b6dcbc
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# WM_ 訊息：S
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列對應項目對應至函式原型。  
  
|對應項目|函式原型|  
|----------|----------|  
|ON\_WM\_SETCURSOR\( \)|afx\_msg BOOL [OnSetCursor](../Topic/CWnd::OnSetCursor.md)\( CWnd\*, UINT, UINT \);|  
|ON\_WM\_SETFOCUS\( \)|afx\_msg void [OnSetFocus](../Topic/CWnd::OnSetFocus.md)\( CWnd\* \);|  
|ON\_WM\_SETTINGCHANGE\( \)|afx\_msg void [OnSettingChange](../Topic/CWnd::OnSettingChange.md)\( UINT uFlags, LPCTSTR lpszSection \);|  
|ON\_WM\_SHOWWINDOW\( \)|afx\_msg void [OnShowWindow](../Topic/CWnd::OnShowWindow.md)\( BOOL, UINT \);|  
|ON\_WM\_SIZE\( \)|afx\_msg void [OnSize](../Topic/CWnd::OnSize.md)\( UINT, int, int \);|  
|ON\_WM\_SIZECLIPBOARD\( \)|afx\_msg void [OnSizeClipboard](../Topic/CWnd::OnSizeClipboard.md)\( CWnd\*, HANDLE \);|  
|ON\_WM\_SIZING\( \)|afx\_msg void [OnSizing](../Topic/CWnd::OnSizing.md)\( UINT, LPRECT \);|  
|ON\_WM\_SPOOLERSTATUS\( \)|afx\_msg void [OnSpoolerStatus](../Topic/CWnd::OnSpoolerStatus.md)\( UINT, UINT \);|  
|ON\_WM\_STYLECHANGED\( \)|afx\_msg void [OnStyleChanged](../Topic/CWnd::OnStyleChanged.md)\( int, LPSTYLESTRUCT \);|  
|ON\_WM\_STYLECHANGING\( \)|afx\_msg void [OnStyleChanging](../Topic/CWnd::OnStyleChanging.md)\( int, LPSTYLESTRUCT \);|  
|ON\_WM\_SYSCHAR\( \)|afx\_msg void [OnSysChar](../Topic/CWnd::OnSysChar.md)\( UINT, UINT, UINT \);|  
|ON\_WM\_SYSCOLORCHANGE\( \)|afx\_msg void [OnSysColorChange](../Topic/CWnd::OnSysColorChange.md)\( \);|  
|ON\_WM\_SYSCOMMAND\( \)|afx\_msg void [OnSysCommand](../Topic/CWnd::OnSysCommand.md)\( UINT, LONG \);|  
|ON\_WM\_SYSDEADCHAR\( \)|afx\_msg void [OnSysDeadChar](../Topic/CWnd::OnSysDeadChar.md)\( UINT, UINT, UINT \);|  
|ON\_WM\_SYSKEYDOWN\( \)|afx\_msg void [OnSysKeyDown](../Topic/CWnd::OnSysKeyDown.md)\( UINT, UINT, UINT \);|  
|ON\_WM\_SYSKEYUP\( \)|afx\_msg void [OnSysKeyUp](../Topic/CWnd::OnSysKeyUp.md)\( UINT, UINT, UINT \);|  
  
## 請參閱  
 [訊息對應](../../mfc/reference/message-maps-mfc.md)   
 [WM\_ 訊息的處理常式](../../mfc/reference/handlers-for-wm-messages.md)
---
title: "滑桿通知訊息 | Microsoft Docs"
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
  - "CSliderCtrl 類別, 告知"
  - "訊息, 告知"
  - "告知, CSliderCtrl"
  - "滑桿, 通知訊息"
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 滑桿通知訊息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

滑桿控制項傳送父 `WM_HSCROLL` 或 `WM_VSCROLL` 訊息通知它的父視窗使用者動作，依據滑桿控制項的方向。  若要處理這些訊息，請將 `WM_HSCROLL` 和 `WM_VSCROLL` 訊息的處理常式加入至父視窗。  [OnHScroll](../Topic/CWnd::OnHScroll.md) 和 [OnVScroll](../Topic/CWnd::OnVScroll.md) 成員函式將透過通知程式碼、滑桿位置和指標至 [CSliderCtrl](../mfc/reference/csliderctrl-class.md) 物件。  請注意指標是型別 **CScrollBar \*** ，即使它指向 `CSliderCtrl` 物件。  如果您需要管理滑桿控制項，您可能需要會將這個角色指標。  
  
 使用捲軸通知程式碼，而不是，滑桿控制項傳送不同通知程式碼。  滑桿控制項傳送 **TB\_BOTTOMTB\_LINEDOWN**，，，， **TB\_LINEUP**和 **TB\_TOP** 通知程式碼可使用鍵盤時，只有在使用者與滑桿控制項互動。  當使用者使用滑鼠時， **TB\_THUMBPOSITION** 和 **TB\_THUMBTRACK** 通知訊息只傳送。  **TB\_ENDTRACK**和 **TB\_PAGEDOWN**和 **TB\_PAGEUP** 通知程式碼在這兩種情況下傳送。  
  
 下表列出滑桿控制項通知訊息和事件 \(虛擬按鍵或滑鼠事件\) 該原因要傳送的通知。\(標準虛擬按鍵碼的清單，請參閱 Winuser.h。\)  
  
|通知訊息|造成事件通知的傳送|  
|----------|---------------|  
|**TB\_BOTTOM**|**VK\_END**|  
|**TB\_ENDTRACK**|`WM_KEYUP` \(使用者釋放傳送相關的虛擬按鍵碼\) 的索引鍵|  
|**TB\_LINEDOWN**|**VK\_RIGHT** 和 **VK\_DOWN**|  
|**TB\_LINEUP**|**VK\_LEFT** 和 **VK\_UP**|  
|**TB\_PAGEDOWN**|**VK\_NEXT** \(使用者按一下的或滑桿的右下方\)|  
|**TB\_PAGEUP**|**VK\_PRIOR** \(使用者按一下的或滑桿左邊上\)|  
|**TB\_THUMBPOSITION**|`WM_LBUTTONUP` 在 **TB\_THUMBTRACK** 通知訊息之後|  
|**TB\_THUMBTRACK**|滑桿移動 \(使用者拖曳滑桿\)|  
|**TB\_TOP**|**VK\_HOME**|  
  
## 請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)
---
title: 滑桿通知訊息 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], notifications
- slider controls [MFC], notification messages
- messages, notification
- notifications [MFC], CSliderCtrl
ms.assetid: b9121104-3889-4a10-92bf-f3723f1af9d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c383458905d16dda935254e56a5aa9f56a153e83
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956157"
---
# <a name="slider-notification-messages"></a>滑桿通知訊息
滑桿控制項會傳送父系 WM_HSCROLL 或 WM_VSCROLL 訊息的滑桿控制項的方向而定，以通知它的父視窗的使用者動作。 若要處理這些訊息，加入處理常式的 WM_HSCROLL 和 WM_VSCROLL 訊息給父視窗。 [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../mfc/reference/cwnd-class.md#onvscroll)通知程式碼、 滑桿和指標的位置，會傳遞給成員函式[CSliderCtrl](../mfc/reference/csliderctrl-class.md)物件。 請注意，指標類型為`CScrollBar *`儘管它指向`CSliderCtrl`物件。 您可能需要類型轉換這個指標，如果您需要管理滑桿控制項。  
  
 而不是使用捲軸告知程式碼，滑桿會傳送一組不同的告知程式碼。 滑桿控制項在透過鍵盤滑桿控制項與使用者互動時，才會傳送 TB_BOTTOM、 TB_LINEDOWN、 TB_LINEUP 和 TB_TOP 告知程式碼。 當使用者使用滑鼠時，才會傳送 TB_THUMBPOSITION 和 TB_THUMBTRACK 通知訊息。 TB_ENDTRACK、 TB_PAGEDOWN 和 TB_PAGEUP 告知程式碼會以兩種情況下傳送。  
  
 下表列出滑桿控制項通知訊息和造成傳送通知的事件 （虛擬按鍵碼或滑鼠事件）。 (如需標準虛擬按鍵碼的清單，請參閱 Winuser.h.)。  
  
|通知訊息|導致傳送通知的事件|  
|--------------------------|-------------------------------------------|  
|TB_BOTTOM|VK_END|  
|TB_ENDTRACK|WM_KEYUP （使用者發行傳送相關的虛擬按鍵碼的索引鍵）|  
|TB_LINEDOWN|VK_RIGHT 或 VK_DOWN|  
|TB_LINEUP|VK_LEFT 或 VK_UP|  
|TB_PAGEDOWN|VK_NEXT （使用者所按下或右邊的滑桿的通道）|  
|TB_PAGEUP|VK_PRIOR （使用者所按的上方或左側的滑桿的通道）|  
|TB_THUMBPOSITION|WM_LBUTTONUP 下 TB_THUMBTRACK 通知訊息|  
|TB_THUMBTRACK|滑塊移動（用戶拖動滑塊）|  
|TB_TOP|VK_HOME|  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)


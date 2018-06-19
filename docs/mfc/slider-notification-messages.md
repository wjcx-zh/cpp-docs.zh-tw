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
ms.openlocfilehash: b003e23a1fef2b44600b9fd15dfe4ca541df5369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381975"
---
# <a name="slider-notification-messages"></a>滑桿通知訊息
滑桿控制項的使用者動作其父視窗會傳送通知父`WM_HSCROLL`或`WM_VSCROLL`的滑桿控制項的方向而定的訊息。 若要處理這些訊息，加入處理常式`WM_HSCROLL`和`WM_VSCROLL`父視窗的訊息。 [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll)和[OnVScroll](../mfc/reference/cwnd-class.md#onvscroll)通知程式碼、 滑桿和指標的位置，會傳遞給成員函式[CSliderCtrl](../mfc/reference/csliderctrl-class.md)物件。 請注意，指標類型為**CScrollBar \*** 儘管它指向`CSliderCtrl`物件。 您可能需要類型轉換這個指標，如果您需要管理滑桿控制項。  
  
 而不是使用捲軸告知程式碼，滑桿會傳送一組不同的告知程式碼。 滑桿控制項會傳送**TB_BOTTOM**， **TB_LINEDOWN**， **TB_LINEUP**，和**TB_TOP**只在使用者互動時，通知代碼與滑桿控制項，使用鍵盤。 **TB_THUMBPOSITION**和**TB_THUMBTRACK**使用者使用滑鼠時，才會傳送通知訊息。 **TB_ENDTRACK**， **TB_PAGEDOWN**，和**TB_PAGEUP**告知程式碼會傳送這兩種情況。  
  
 下表列出滑桿控制項通知訊息和造成傳送通知的事件 （虛擬按鍵碼或滑鼠事件）。 (如需標準虛擬按鍵碼的清單，請參閱 Winuser.h.)。  
  
|通知訊息|導致傳送通知的事件|  
|--------------------------|-------------------------------------------|  
|**TB_BOTTOM**|**VK_END**|  
|**TB_ENDTRACK**|`WM_KEYUP` （使用者發行傳送相關的虛擬按鍵碼的索引鍵）|  
|**TB_LINEDOWN**|**VK_RIGHT**或**VK_DOWN**|  
|**TB_LINEUP**|**VK_LEFT**或**VK_UP**|  
|**TB_PAGEDOWN**|**VK_NEXT** （使用者所按下或右邊的滑桿的通道）|  
|**TB_PAGEUP**|**VK_PRIOR** （使用者所按的上方或左側的滑桿的通道）|  
|**TB_THUMBPOSITION**|`WM_LBUTTONUP` 遵循**TB_THUMBTRACK**通知訊息|  
|**TB_THUMBTRACK**|（使用者拖曳滑桿）|  
|**TB_TOP**|**VK_HOME**|  
  
## <a name="see-also"></a>另請參閱  
 [使用 CSliderCtrl](../mfc/using-csliderctrl.md)   
 [控制項](../mfc/controls-mfc.md)


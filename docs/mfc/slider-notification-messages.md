---
title: 滑桿通知訊息 |Microsoft Docs
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
ms.openlocfilehash: 775ca98ff19266343631ff54bac16bebfff9e264
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399531"
---
# <a name="slider-notification-messages"></a>滑桿通知訊息

滑桿控制項告知它的父視窗的使用者動作所傳送的父代時傳遞 WM_HSCROLL 或 WM_VSCROLL 訊息、 根據滑桿控制項的方向。 若要處理這些訊息，新增處理常式時傳遞 WM_HSCROLL 和 WM_VSCROLL 訊息至父視窗。 [OnHScroll](../mfc/reference/cwnd-class.md#onhscroll)並[OnVScroll](../mfc/reference/cwnd-class.md#onvscroll)成員函式會通知程式碼、 滑桿和指標的位置傳遞[CSliderCtrl](../mfc/reference/csliderctrl-class.md)物件。 請注意，指標是型別的`CScrollBar *`即使它指向`CSliderCtrl`物件。 您可能需要轉換 this 指標的類型，如果您要管理滑桿控制項。

而不是使用捲軸通知程式碼，滑桿控制項會傳送一組不同的通知程式碼。 只有在使用者使用鍵盤進行互動的滑桿控制項時，滑桿控制項就會傳送 TB_BOTTOM、 TB_LINEDOWN、 TB_LINEUP 和 TB_TOP 通知程式碼。 當使用者使用滑鼠時，才會傳送 TB_THUMBPOSITION 和 TB_THUMBTRACK 通知訊息。 在這兩種情況下，會傳送 TB_ENDTRACK、 TB_PAGEDOWN 和 TB_PAGEUP 通知程式碼。

下表列出滑桿控制項通知訊息和導致傳送通知的事件 （虛擬按鍵碼或滑鼠事件）。 (如需標準虛擬按鍵碼的清單，請參閱 Winuser.h.)。

|通知訊息|導致傳送通知的事件|
|--------------------------|-------------------------------------------|
|TB_BOTTOM|VK_END|
|TB_ENDTRACK|WM_KEYUP （使用者發行傳送相關的虛擬按鍵碼的索引鍵）|
|TB_LINEDOWN|VK_RIGHT 或 VK_DOWN|
|TB_LINEUP|VK_LEFT 或 VK_UP|
|TB_PAGEDOWN|VK_NEXT （使用者所按下或右邊的滑桿的通道）|
|TB_PAGEUP|VK_PRIOR （使用者會按一下上方或左側的滑桿的通道）|
|TB_THUMBPOSITION|WM_LBUTTONUP 遵循 TB_THUMBTRACK 通知訊息|
|TB_THUMBTRACK|滑塊移動（用戶拖動滑塊）|
|TB_TOP|VK_HOME|

## <a name="see-also"></a>另請參閱

[使用 CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)


---
title: 從通用控制項接收告知
ms.date: 11/04/2016
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
helpviewer_keywords:
- OnNotify method [MFC]
- common controls [MFC], notifications
- ON_NOTIFY macro [MFC]
- controls [MFC], notifications
- receiving notifications from common controls
- notifications [MFC], common controls
- Windows common controls [MFC], notifications
- WM_NOTIFY message
ms.assetid: 50194592-d60d-44d0-8ab3-338a2a2c63e7
ms.openlocfilehash: fb923374866aa8348f9b895c9b97915817564883
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287423"
---
# <a name="receiving-notification-from-common-controls"></a>從通用控制項接收告知

通用控制項是當控制項中發生事件時 (例如來自使用者的輸入) 傳送通知訊息給父視窗的子視窗。

應用程式仰賴這些通知訊息來判斷使用者要其採取的動作。 最常見的控制項以 WM_NOTIFY 訊息傳送通知訊息。 Windows 控制項以 WM_COMMAND 訊息傳送大部分的通知訊息。 [Cwnd:: Onnotify](../mfc/reference/cwnd-class.md#onnotify) WM_NOTIFY 訊息處理常式。 如同使用 `CWnd::OnCommand`，`OnNotify` 的實作會分派通知訊息至 `OnCmdMsg` 供在訊息對應中處理。 處理通知的訊息對應項目是 ON_NOTIFY。 如需詳細資訊，請參閱[技術提示 61:ON_NOTIFY 和 WM_NOTIFY 訊息](../mfc/tn061-on-notify-and-wm-notify-messages.md)。

此外，衍生的類別可以使用「訊息反映」處理其本身的通知訊息。 如需詳細資訊，請參閱[技術提示 62:訊息反映的 Windows 控制項](../mfc/tn062-message-reflection-for-windows-controls.md)。

## <a name="retrieving-the-cursor-position-in-a-notification-message"></a>擷取通知訊息中的游標位置

有時候，當通用控制項收到特定通知訊息時，決定游標的目前位置會很有用。 比方說，它會判斷目前的游標位置，當通用控制項收到 NM_RCLICK 告知訊息時，很有幫助。

有一簡單方式可透過呼叫 `CWnd::GetCurrentMessage`來完成此項。 不過，這個方法只有在訊息送出時才會擷取游標位置。 因為游標可能已經移動，所以您必須呼叫傳送訊息之`CWnd::GetCursorPos`來取得目前的游標位置。

> [!NOTE]
>  您應該只在訊息處理常式內呼叫 `CWnd::GetCurrentMessage`。

（在此範例中，NM_RCLICK） 的通知訊息處理常式的主體中加入下列程式碼：

[!code-cpp[NVC_MFCControlLadenDialog#4](../mfc/codesnippet/cpp/receiving-notification-from-common-controls_1.cpp)]

此時，滑鼠游標位置是儲存在 `cursorPos` 物件中。

## <a name="see-also"></a>另請參閱

[建立及使用控制項](../mfc/making-and-using-controls.md)<br/>
[控制項](../mfc/controls-mfc.md)

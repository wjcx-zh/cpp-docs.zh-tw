---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 292a1c6606585dc0694ee678ba8bc9b5fbc42681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261442"
---
# <a name="notifyhandler"></a>NotifyHandler

訊息對應中 NOTIFY_HANDLER 巨集的第三個參數所識別的函式名稱。

## <a name="syntax"></a>語法

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>參數

*idCtrl*<br/>
傳送訊息的控制項識別項。

*pnmh*<br/>
位址[NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr)結構，包含通知程式碼和其他資訊。 對於某些通知的訊息，此參數會指向較大的結構，其`NMHDR`做為其第一個成員的結構。

*bHandled*<br/>
訊息對應集*bHandled*設為 TRUE 之前*NotifyHandler*呼叫。 如果*NotifyHandler*不會完全處理訊息，它應該設定*bHandled*來**FALSE**以指出訊息必須進一步處理。

## <a name="return-value"></a>傳回值

訊息處理的結果。 0，表示成功。

## <a name="remarks"></a>備註

如需訊息對應中使用此訊息處理常式的範例，請參閱[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)<br/>
[訊息對應](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)

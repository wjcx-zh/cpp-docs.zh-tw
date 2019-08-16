---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492315"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`這是訊息對應中 MESSAGE_HANDLER 宏的第二個參數所識別的函式名稱。

## <a name="syntax"></a>語法

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>參數

*uMsg*<br/>
指定訊息。

*wParam*<br/>
其他訊息特定資訊。

*lParam*<br/>
其他訊息特定資訊。

*bHandled*<br/>
在呼叫之前`MessageHandler` , 訊息對應會將*bHandled*設定為 TRUE。 如果`MessageHandler`未完整處理訊息, 則應該將*bHandled*設定為 FALSE, 以指出訊息需要進一步處理。

## <a name="return-value"></a>傳回值

訊息處理的結果。 如果成功, 則為0。

## <a name="remarks"></a>備註

如需在訊息對應中使用此訊息處理常式的範例, 請參閱[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)<br/>
[訊息對應](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

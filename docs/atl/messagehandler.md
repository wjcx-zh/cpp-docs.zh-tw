---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageHandler
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: deb217e2f889d30ab5c4caa7d9812d5e612dcb62
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299344"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` 是 MESSAGE_HANDLER 巨集訊息對應中的第二個參數所識別的函式的名稱。

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
指定的訊息。

*wParam*<br/>
其他特定訊息資訊。

*lParam*<br/>
其他特定訊息資訊。

*bHandled*<br/>
訊息對應集*bHandled*設為 TRUE 之前`MessageHandler`呼叫。 如果`MessageHandler`完全不會處理訊息，它應該設定*bHandled*為 FALSE，以指出需要進一步處理的訊息。

## <a name="return-value"></a>傳回值

訊息處理的結果。 0，表示成功。

## <a name="remarks"></a>備註

如需訊息對應中使用此訊息處理常式的範例，請參閱[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)<br/>
[訊息對應](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)

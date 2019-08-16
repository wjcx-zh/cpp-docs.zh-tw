---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492460"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`這是訊息對應中 COMMAND_HANDLER 宏的第三個參數所識別的函式。

## <a name="syntax"></a>語法

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>參數

*wNotifyCode*<br/>
通知碼。

*wID*<br/>
功能表項目、控制項或快速鍵的識別碼。

*hWndCtl*<br/>
視窗控制項的控制碼。

*bHandled*<br/>
在呼叫之前`CommandHandler` , 訊息對應會將*bHandled*設定為 TRUE。 如果`CommandHandler`未完整處理訊息, 則應該將*bHandled*設定為 FALSE, 以指出訊息需要進一步處理。

## <a name="return-value"></a>傳回值

訊息處理的結果。 如果成功, 則為0。

## <a name="remarks"></a>備註

如需在訊息對應中使用此訊息處理常式的範例, 請參閱[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)<br/>
[訊息對應](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

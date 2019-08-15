---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 16fb330d2da83ddfd013e33a2d4b688b2711103b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492307"
---
# <a name="notifyhandler"></a>NotifyHandler

訊息對應中 NOTIFY_HANDLER 宏的第三個參數所識別的函式名稱。

## <a name="syntax"></a>語法

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>參數

*idCtrl*<br/>
傳送訊息之控制項的識別碼。

*pnmh*<br/>
[NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr)結構的位址, 其中包含通知碼和其他資訊。 對於某些通知訊息, 此參數會`NMHDR`指向結構為其第一個成員的較大結構。

*bHandled*<br/>
在呼叫*NotifyHandler*之前, 訊息對應會將*BHANDLED*設定為 TRUE。 如果*NotifyHandler*未完整處理訊息, 則應該將*BHandled*設定為**FALSE** , 以指出訊息需要進一步處理。

## <a name="return-value"></a>傳回值

訊息處理的結果。 如果成功, 則為0。

## <a name="remarks"></a>備註

如需在訊息對應中使用此訊息處理常式的範例, 請參閱[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。

## <a name="see-also"></a>另請參閱

[實作視窗](../atl/implementing-a-window.md)<br/>
[訊息對應](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)

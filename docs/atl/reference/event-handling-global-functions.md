---
title: 事件處理全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: bb109c63b497420ad6e797cd8e0b366ce4dc0475
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292220"
---
# <a name="event-handling-global-functions"></a>事件處理全域函式

此函式會提供事件處理常式。

> [!IMPORTANT]
>  下表所列的函式不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等候物件收到信號，同時視需要分派視窗訊息。|

## <a name="requirements"></a>需求

**標頭：** atlbase.h

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop

等候發出物件通知，同時視需要分派視窗訊息。

> [!IMPORTANT]
>  此函式不能在 Windows 執行階段中執行的應用程式。

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>參數

*hEvent*<br/>
[in]要等候的物件控制代碼。

### <a name="return-value"></a>傳回值

如果物件已收到訊號，則傳回 TRUE。

### <a name="remarks"></a>備註

如果您想要等待物件的事件發生，並收到發生，但允許在等待時分派視窗訊息，這非常有用。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)

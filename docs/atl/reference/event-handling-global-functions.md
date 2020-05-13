---
title: 事件處理全域函數
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330140"
---
# <a name="event-handling-global-functions"></a>事件處理全域函數

此函數提供事件處理程式。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等待物件發出信號,同時根據需要調度視窗消息。|

## <a name="requirements"></a>需求

**標題:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWait與訊息迴圈

等候發出物件通知，同時視需要分派視窗訊息。

> [!IMPORTANT]
> 此函數不能在 Windows 運行時中執行的應用程式中使用。

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>參數

*hEvent*<br/>
[在]要等待的物件的句柄。

### <a name="return-value"></a>傳回值

如果物件已發出信號,則返回 TRUE。

### <a name="remarks"></a>備註

如果要等待物件的事件發生並收到通知,但允許在等待時調度視窗消息,則此功能非常有用。

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)

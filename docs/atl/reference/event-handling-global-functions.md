---
title: 事件處理全域函式
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: fde93415640ef7fa460bb363af4c3cb14b356061
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833448"
---
# <a name="event-handling-global-functions"></a>事件處理全域函式

此函數會提供事件處理常式。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等候物件收到信號，同時視需要分派視窗訊息。|

## <a name="requirements"></a>規格需求

**標頭：** atlbase.h。h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a> AtlWaitWithMessageLoop

等候發出物件通知，同時視需要分派視窗訊息。

> [!IMPORTANT]
> 在 Windows 執行階段中執行的應用程式不能使用這個函數。

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>參數

*hEvent*<br/>
在要等候的物件控制碼。

### <a name="return-value"></a>傳回值

如果物件已收到信號，則傳回 TRUE。

### <a name="remarks"></a>備註

如果您想要等候物件的事件發生，並收到它的通知，但允許在等候時分派視窗訊息，這會很有用。

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)

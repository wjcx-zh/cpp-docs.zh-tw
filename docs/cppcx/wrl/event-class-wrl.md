---
title: 事件類別 (WRL)
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
helpviewer_keywords:
- Microsoft::WRL::Wrappers::Event class
- Microsoft::WRL::Wrappers::Event::Event, constructor
- Microsoft::WRL::Wrappers::Event::operator= operator
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
ms.openlocfilehash: 2d36b4fa3d1824f43e0cfafe55c439a6bdeccb6f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784644"
---
# <a name="event-class-wrl"></a>事件類別 (WRL)

表示事件。

## <a name="syntax"></a>語法

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                   | 描述
---------------------- | ------------------------------------------------
[Event::Event](#event) | 初始化 `Event` 類別的新執行個體。

### <a name="public-operators"></a>公用運算子

名稱                                 | 描述
------------------------------------ | ------------------------------------------------------------------------
[Event::operator=](#operator-assign) | 指派指定的`Event`參考目前`Event`執行個體。

## <a name="inheritance-hierarchy"></a>繼承階層

`HandleT`

`Event`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="event"></a>Event::Event

初始化 `Event` 類別的新執行個體。

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
事件的控制代碼。 根據預設， *h*初始化為`nullptr`。

## <a name="operator-assign"></a>Event::operator=

指派指定的`Event`參考目前`Event`執行個體。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
若要為右值參考`Event`執行個體。

### <a name="return-value"></a>傳回值

目前的指標`Event`執行個體。

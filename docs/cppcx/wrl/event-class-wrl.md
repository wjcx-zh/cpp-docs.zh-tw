---
title: Event 類別（WRL）
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
ms.openlocfilehash: 27a90bb801d1b6869b2391227464bb215dd42538
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220479"
---
# <a name="event-class-wrl"></a>Event 類別（WRL）

表示事件。

## <a name="syntax"></a>語法

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                   | 說明
---------------------- | ------------------------------------------------
[Event：： Event](#event) | 初始化 `Event` 類別的新執行個體。

### <a name="public-operators"></a>公用運算子

名稱                                 | 說明
------------------------------------ | ------------------------------------------------------------------------
[Event：： operator =](#operator-assign) | 將指定的 `Event` 參考指派給目前的 `Event` 實例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HandleT`

`Event`

## <a name="requirements"></a>需求

**標頭：** corewrappers。h

**命名空間：** Microsoft：： WRL：：包裝函式

## <a name="eventevent"></a><a name="event"></a>Event：： Event

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
事件的控制代碼。 根據預設， *h*會初始化為 **`nullptr`** 。

## <a name="eventoperator"></a><a name="operator-assign"></a>Event：： operator =

將指定的 `Event` 參考指派給目前的 `Event` 實例。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*h*<br/>
實例的右值參考 `Event` 。

### <a name="return-value"></a>傳回值

目前實例的指標 `Event` 。

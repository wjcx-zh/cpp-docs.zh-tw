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
ms.openlocfilehash: 85b4c2d1f1a27e90a65e47aa749e079f4aa08739
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371527"
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
[事件:事件](#event) | 將 `Event` 類別的新執行個體初始化。

### <a name="public-operators"></a>公用運算子

名稱                                 | 描述
------------------------------------ | ------------------------------------------------------------------------
[事件::操作員*](#operator-assign) | 將指定的`Event`引用分配給`Event`當前 實例。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`HandleT`

`Event`

## <a name="requirements"></a>需求

**標題:** 核心包裝.h

**命名空間:** 微軟::WRL:包裝

## <a name="eventevent"></a><a name="event"></a>事件:事件

將 `Event` 類別的新執行個體初始化。

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
事件的控制代碼。 預設情況下 *,h*初始`nullptr`化到 。

## <a name="eventoperator"></a><a name="operator-assign"></a>事件::操作員*

將指定的`Event`引用分配給`Event`當前 實例。

```cpp
WRL_NOTHROW Event& operator=(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>參數

*H*<br/>
實例的`Event`rvalue 引用。

### <a name="return-value"></a>傳回值

指向當前`Event`實例的指標。

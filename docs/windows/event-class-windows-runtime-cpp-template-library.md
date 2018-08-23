---
title: 事件類別 （Windows 執行階段 c + + 樣板程式庫） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event
dev_langs:
- C++
ms.assetid: 55dfc9fc-62d4-4bb2-9d85-5b6dd88569e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b40e9c5e04c21cdbcc56581e02751edc84e4617d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606285"
---
# <a name="event-class-windows-runtime-c-template-library"></a>Event 類別 (Windows 執行階段 C++ 樣板程式庫)

表示事件。

## <a name="syntax"></a>語法

```cpp
class Event : public HandleT<HandleTraits::EventTraits>;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[Event::Event 建構函式 (Windows 執行階段 C++ 範本庫)](../windows/event-event-constructor-windows-runtime-cpp-template-library.md)|初始化的新執行個體**事件**類別。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[Event::operator= 運算子](../windows/event-operator-assign-operator.md)|指派指定的**事件**參考目前**事件**執行個體。|

## <a name="inheritance-hierarchy"></a>繼承階層

`HandleT`

`Event`

## <a name="requirements"></a>需求

**標頭：** corewrappers.h

**命名空間：** Microsoft::WRL::Wrappers

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)
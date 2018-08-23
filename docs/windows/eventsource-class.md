---
title: EventSource 類別 |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8805547c5803ae665178330063e6b77b1b3c662e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596207"
---
# <a name="eventsource-class"></a>EventSource 類別

代表非 agile 的事件。 **EventSource**成員函式加入、 移除及叫用事件處理常式。 針對敏捷式軟體開發的事件，使用[AgileEventSource](agileeventsource-class.md)。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>參數

*TDelegateInterface*  
要委派，表示事件處理常式的介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[EventSource::EventSource 建構函式](../windows/eventsource-eventsource-constructor.md)|初始化的新執行個體**EventSource**類別。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[EventSource::Add 方法](../windows/eventsource-add-method.md)|將附加事件處理常式，以指定的委派介面來表示目前的事件處理常式的集合**EventSource**物件。|
|[EventSource::GetSize 方法](../windows/eventsource-getsize-method.md)|擷取與目前相關聯的事件處理常式數目**EventSource**物件|
|[EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)|呼叫目前相關聯的每個事件處理常式**EventSource**物件使用指定的引數型別和引數。|
|[EventSource::Remove 方法](../windows/eventsource-remove-method.md)|刪除從目前與相關聯的事件處理常式的集合指定的事件註冊語彙基元所代表的事件處理常式**EventSource**物件。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[EventSource::addRemoveLock_ 資料成員](../windows/eventsource-addremovelock-data-member.md)|同步存取[targets_](../windows/eventsource-targets-data-member.md)陣列時加入、 移除或叫用事件處理常式。|
|[EventSource::targets_ 資料成員](../windows/eventsource-targets-data-member.md)|一或多個事件處理常式的陣列。|
|[EventSource::targetsPointerLock_ 資料成員](../windows/eventsource-targetspointerlock-data-member.md)|同步處理正在加入此 eventsource 的事件處理常式、 同時也已移除，或叫用的內部資料成員的存取權。|

## <a name="inheritance-hierarchy"></a>繼承階層

`EventSource`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)  
[AgileEventSource 類別](agileeventsource-class.md)
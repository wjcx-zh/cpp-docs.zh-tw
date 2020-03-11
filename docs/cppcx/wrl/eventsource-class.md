---
title: EventSource 類別
ms.date: 09/12/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
- event/Microsoft::WRL::EventSource::Add
- event/Microsoft::WRL::EventSource::addRemoveLock_
- event/Microsoft::WRL::EventSource::EventSource
- event/Microsoft::WRL::EventSource::GetSize
- event/Microsoft::WRL::EventSource::InvokeAll
- event/Microsoft::WRL::EventSource::Remove
- event/Microsoft::WRL::EventSource::targets_
- event/Microsoft::WRL::EventSource::targetsPointerLock_
helpviewer_keywords:
- Microsoft::WRL::EventSource class
- Microsoft::WRL::EventSource::Add method
- Microsoft::WRL::EventSource::addRemoveLock_ data member
- Microsoft::WRL::EventSource::EventSource, constructor
- Microsoft::WRL::EventSource::GetSize method
- Microsoft::WRL::EventSource::InvokeAll method
- Microsoft::WRL::EventSource::Remove method
- Microsoft::WRL::EventSource::targets_ data member
- Microsoft::WRL::EventSource::targetsPointerLock_ data member
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
ms.openlocfilehash: 1350e51ff609a888b6a8ad6841be6856b68c7994
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865726"
---
# <a name="eventsource-class"></a>EventSource 類別

表示非 agile 事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。 針對 agile 事件，請使用[AgileEventSource](agileeventsource-class.md)。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>參數

*TDelegateInterface*<br/>
委派的介面，表示事件處理常式。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                                     | 描述                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource：： EventSource](#eventsource) | 將 `EventSource` 類別的新執行個體初始化。 |

### <a name="public-methods"></a>公用方法

| 名稱                                 | 描述                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource：： Add](#add)             | 將指定的委派介面所表示的事件處理常式附加至目前 `EventSource` 物件的事件處理常式集合。                     |
| [EventSource：： GetSize](#getsize)     | 抓取與目前 `EventSource` 物件相關聯的事件處理常式數目。                                                                         |
| [EventSource：： InvokeAll](#invokeall) | 使用指定的引數類型和引數，呼叫與目前 `EventSource` 物件相關聯的每個事件處理常式。                                      |
| [EventSource：： Remove](#remove)       | 從與目前 `EventSource` 物件相關聯的事件處理常式集合中，刪除指定的事件註冊 token 所表示的事件處理常式。 |

### <a name="protected-data-members"></a>受保護的資料成員

| 名稱                                                    | 描述                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource：： addRemoveLock_](#addremovelock)           | 加入、移除或叫用事件處理常式時，同步處理[targets_](#targets)陣列的存取權。                          |
| [EventSource：： targets_](#targets)                       | 一或多個事件處理常式的陣列。                                                                                           |
| [EventSource：： targetsPointerLock_](#targetspointerlock) | 即使加入、移除或叫用此 EventSource 的事件處理常式，也會同步處理內部資料成員的存取。 |

## <a name="inheritance-hierarchy"></a>繼承階層

`EventSource`

## <a name="requirements"></a>需求

**Header：** 事件。h

**命名空間：** Microsoft::WRL

## <a name="add"></a>EventSource：： Add

將指定的委派介面所表示的事件處理常式附加至目前 `EventSource` 物件的事件處理常式集合。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>參數

*delegateInterface*<br/>
委派物件的介面，表示事件處理常式。

*token*<br/>
當此作業完成時，表示事件的控制碼。 使用此 token 做為[Remove （）](#remove)方法的參數，以捨棄事件處理常式。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="addremovelock"></a>EventSource：： addRemoveLock_

加入、移除或叫用事件處理常式時，同步處理[targets_](#targets)陣列的存取權。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource：： EventSource

將 `EventSource` 類別的新執行個體初始化。

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource：： GetSize

抓取與目前 `EventSource` 物件相關聯的事件處理常式數目。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>傳回值

[Targets_](#targets)中的事件處理常式數目。

## <a name="invokeall"></a>EventSource：： InvokeAll

使用指定的引數類型和引數，呼叫與目前 `EventSource` 物件相關聯的每個事件處理常式。

```cpp
void InvokeAll();
template <
   typename T0
>
void InvokeAll(
   T0arg0
);
template <
   typename T0,
   typename T1
>
void InvokeAll(
   T0arg0,
   T1arg1
);
template <
   typename T0,
   typename T1,
   typename T2
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8
);
template <
   typename T0,
   typename T1,
   typename T2,
   typename T3,
   typename T4,
   typename T5,
   typename T6,
   typename T7,
   typename T8,
   typename T9
>
void InvokeAll(
   T0arg0,
   T1arg1,
   T2arg2,
   T3arg3,
   T4arg4,
   T5arg5,
   T6arg6,
   T7arg7,
   T8arg8,
   T9arg9
);
```

### <a name="parameters"></a>參數

*T0*<br/>
預備事件處理常式引數的類型。

*T1*<br/>
第一個事件處理常式引數的類型。

*T2*<br/>
第二個事件處理常式引數的類型。

*T3*<br/>
第三個事件處理常式引數的類型。

*T4*<br/>
第四個事件處理常式引數的類型。

*T5*<br/>
第五個事件處理常式引數的類型。

*T6*<br/>
第六個事件處理常式引數的類型。

*T7*<br/>
第七個事件處理常式引數的類型。

*T8*<br/>
第八個事件處理常式引數的類型。

*T9*<br/>
第九個事件處理常式引數的類型。

*arg0*<br/>
預備事件處理常式引數。

*arg1*<br/>
第一個事件處理常式引數。

*arg2*<br/>
第二個事件處理常式引數。

*arg3*<br/>
第三個事件處理常式引數。

*arg4*<br/>
第四個事件處理常式引數。

*arg5*<br/>
第五個事件處理常式引數。

*arg6*<br/>
第六個事件處理常式引數。

*arg7*<br/>
第七個事件處理常式引數。

*arg8*<br/>
第八個事件處理常式引數。

*arg9*<br/>
第九個事件處理常式引數。

## <a name="remove"></a>EventSource：： Remove

從與目前 `EventSource` 物件相關聯的事件處理常式集合中，刪除指定的事件註冊 token 所表示的事件處理常式。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>參數

*token*<br/>
表示事件處理常式的控制碼。 當事件處理常式由[Add （）](#add)方法註冊時，就會傳回這個 token。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如需 `EventRegistrationToken` 結構的詳細資訊，請參閱**Windows 執行階段**參考檔中的**Windows：： Foundation：： EventRegistrationToken 結構**主題。

## <a name="targets"></a>EventSource：： targets_

一或多個事件處理常式的陣列。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>備註

當目前的 `EventSource` 物件所代表的事件發生時，就會呼叫事件處理常式。

## <a name="targetspointerlock"></a>EventSource：： targetsPointerLock_

即使加入、移除或叫用此 `EventSource` 的事件處理常式，也會同步處理內部資料成員的存取。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```

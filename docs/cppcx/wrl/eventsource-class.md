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
ms.openlocfilehash: e9070fe756410e3e1bb1e5840eb3f06e29c2f46b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784573"
---
# <a name="eventsource-class"></a>EventSource 類別

代表非 agile 的事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。 針對敏捷式軟體開發的事件，使用[AgileEventSource](agileeventsource-class.md)。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>參數

*TDelegateInterface*<br/>
要委派，表示事件處理常式的介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                                     | 描述                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [EventSource::EventSource](#eventsource) | 初始化 `EventSource` 類別的新執行個體。 |

### <a name="public-methods"></a>公用方法

| 名稱                                 | 描述                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::Add](#add)             | 將附加事件處理常式，以指定的委派介面來表示目前的事件處理常式組`EventSource`物件。                     |
| [EventSource::GetSize](#getsize)     | 擷取與目前相關聯的事件處理常式數目`EventSource`物件。                                                                         |
| [EventSource::InvokeAll](#invokeall) | 呼叫目前相關聯的每個事件處理常式`EventSource`物件使用指定的引數型別和引數。                                      |
| [EventSource::Remove](#remove)       | 刪除從目前與相關聯的事件處理常式的集合指定的事件註冊語彙基元所代表的事件處理常式`EventSource`物件。 |

### <a name="protected-data-members"></a>受保護的資料成員

| 名稱                                                    | 描述                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [EventSource::addRemoveLock_](#addremovelock)           | 同步存取[targets_](#targets)陣列時加入、 移除或叫用事件處理常式。                          |
| [EventSource::targets_](#targets)                       | 一或多個事件處理常式的陣列。                                                                                           |
| [EventSource::targetsPointerLock_](#targetspointerlock) | 同步處理正在加入此 eventsource 的事件處理常式、 同時也已移除，或叫用的內部資料成員的存取權。 |

## <a name="inheritance-hierarchy"></a>繼承階層

`EventSource`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft:: wrl

## <a name="add"></a>EventSource::Add

將附加事件處理常式，以指定的委派介面來表示目前的事件處理常式組`EventSource`物件。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>參數

*delegateInterface*<br/>
要委派物件，代表事件處理常式的介面。

*token*<br/>
這項作業完成時，代表事件的控制代碼。 使用此權杖做為參數[remove （)](#remove)捨棄的事件處理常式的方法。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="addremovelock"></a>EventSource::addRemoveLock_

同步存取[targets_](#targets)陣列時加入、 移除或叫用事件處理常式。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsource"></a>EventSource::EventSource

初始化 `EventSource` 類別的新執行個體。

```cpp
EventSource();
```

## <a name="getsize"></a>EventSource::GetSize

擷取與目前相關聯的事件處理常式數目`EventSource`物件。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>傳回值

中的事件處理常式數目[targets_](#targets)。

## <a name="invokeall"></a>EventSource::InvokeAll

呼叫目前相關聯的每個事件處理常式`EventSource`物件使用指定的引數型別和引數。

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
第零個事件處理常式的引數的類型。

*T1*<br/>
第一個事件處理常式引數型別。

*T2*<br/>
第二個事件處理常式引數的型別。

*T3*<br/>
第三個事件處理常式引數的型別。

*T4*<br/>
第四個事件處理常式引數的型別。

*T5*<br/>
第五個事件處理常式引數的型別。

*T6*<br/>
第六個事件處理常式引數的型別。

*T7*<br/>
第七個事件處理常式引數的型別。

*T8*<br/>
第八個事件處理常式的引數的類型。

*T9*<br/>
第九個事件處理常式引數的型別。

*arg0*<br/>
第零個事件處理常式引數。

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

## <a name="remove"></a>EventSource::Remove

刪除從目前與相關聯的事件處理常式的集合指定的事件註冊語彙基元所代表的事件處理常式`EventSource`物件。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>參數

*token*<br/>
代表事件處理常式的控制代碼。 註冊事件處理常式時，傳回這個語彙基元[add （)](#add)方法。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

如需詳細資訊`EventRegistrationToken`結構，請參閱**Windows::Foundation::EventRegistrationToken 結構**中的主題**Windows 執行階段**參考文件。

## <a name="targets"></a>EventSource::targets_

一或多個事件處理常式的陣列。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>備註

當目前由事件`EventSource`物件發生時，會呼叫事件處理常式。

## <a name="targetspointerlock"></a>EventSource::targetsPointerLock_

這個同步處理內部資料成員，即使事件處理常式的存取`EventSource`正在加入、 移除或叫用。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```

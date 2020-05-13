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
ms.openlocfilehash: bb9151e55d133e3e5d8bf10baeb8448101ad6ce0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371532"
---
# <a name="eventsource-class"></a>EventSource 類別

表示非敏捷事件。 `EventSource` 成員函式會新增、移除及叫用事件處理常式。 對於敏捷事件,請使用[敏捷事件源](agileeventsource-class.md)。

## <a name="syntax"></a>語法

```cpp
template<typename TDelegateInterface>
class EventSource;
```

### <a name="parameters"></a>參數

*T委託介面*<br/>
表示事件處理程式的委託的介面。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

| 名稱                                     | 描述                                            |
| ---------------------------------------- | ------------------------------------------------------ |
| [事件來源:事件來源](#eventsource) | 將 `EventSource` 類別的新執行個體初始化。 |

### <a name="public-methods"></a>公用方法

| 名稱                                 | 描述                                                                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [事件來源:新增](#add)             | 將指定委託介面表示的事件處理程式追加到當前`EventSource`物件的事件處理程式集。                     |
| [事件來源:取得 Size](#getsize)     | 檢索與當前`EventSource`物件關聯的事件處理程式數。                                                                         |
| [事件來源::全部呼叫](#invokeall) | 使用指定的參數類型和參數呼叫與`EventSource`當前物件關聯的每個事件處理程式。                                      |
| [事件來源:刪除](#remove)       | 從與當前`EventSource`物件關聯的事件處理程式集中刪除指定事件註冊權杖表示的事件處理程式。 |

### <a name="protected-data-members"></a>受保護的資料成員

| 名稱                                                    | 描述                                                                                                                       |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| [活動來源:addRemoveLock_](#addremovelock)           | 在添加、刪除或調用事件處理程式時同步對[targets_](#targets)陣列的訪問。                          |
| [活動來源::targets_](#targets)                       | 一個或多個事件處理程式的陣列。                                                                                           |
| [活動來源:targetsPointerLock_](#targetspointerlock) | 同步對內部數據成員的訪問,即使正在添加、刪除或調用此事件源的事件處理程式也是如此。 |

## <a name="inheritance-hierarchy"></a>繼承階層架構

`EventSource`

## <a name="requirements"></a>需求

**標題:** 事件.h

**命名空間：** Microsoft::WRL

## <a name="eventsourceadd"></a><a name="add"></a>事件來源:新增

將指定委託介面表示的事件處理程式追加到當前`EventSource`物件的事件處理程式集。

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>參數

*委託介面*<br/>
委託物件的介面,該物件表示事件處理程式。

*權杖*<br/>
此操作完成後,表示事件的句柄。 使用此令牌作為[Remove()](#remove)方法的參數來丟棄事件處理程式。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="eventsourceaddremovelock_"></a><a name="addremovelock"></a>活動來源:addRemoveLock_

在添加、刪除或調用事件處理程式時同步對[targets_](#targets)陣列的訪問。

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="eventsourceeventsource"></a><a name="eventsource"></a>事件來源:事件來源

將 `EventSource` 類別的新執行個體初始化。

```cpp
EventSource();
```

## <a name="eventsourcegetsize"></a><a name="getsize"></a>事件來源:取得 Size

檢索與當前`EventSource`物件關聯的事件處理程式數。

```cpp
size_t GetSize() const;
```

### <a name="return-value"></a>傳回值

[targets_](#targets)中的事件處理程式數。

## <a name="eventsourceinvokeall"></a><a name="invokeall"></a>事件來源::全部呼叫

使用指定的參數類型和參數呼叫與`EventSource`當前物件關聯的每個事件處理程式。

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
第零事件處理程式參數的類型。

*T1*<br/>
第一個事件處理程式參數的類型。

*T2*<br/>
第二個事件處理程式參數的類型。

*T3*<br/>
第三個事件處理程式參數的類型。

*T4*<br/>
第四個事件處理程式參數的類型。

*T5*<br/>
第五個事件處理程式參數的類型。

*T6*<br/>
第六個事件處理程式參數的類型。

*T7*<br/>
第七個事件處理程式參數的類型。

*T8*<br/>
第八個事件處理程式參數的類型。

*T9*<br/>
第九個事件處理程式參數的類型。

*arg0*<br/>
第零事件處理程式參數。

*arg1*<br/>
第一個事件處理程式參數。

*arg2*<br/>
第二個事件處理程式參數。

*arg3*<br/>
第三個事件處理程式參數。

*arg4*<br/>
第四個事件處理程式參數。

*arg5*<br/>
第五個事件處理程式參數。

*arg6*<br/>
第六個事件處理程式參數。

*arg7*<br/>
第七個事件處理程式參數。

*arg8*<br/>
第八個事件處理程式參數。

*arg9*<br/>
第九個事件處理程式參數。

## <a name="eventsourceremove"></a><a name="remove"></a>事件來源:刪除

從與當前`EventSource`物件關聯的事件處理程式集中刪除指定事件註冊權杖表示的事件處理程式。

```cpp
HRESULT Remove(
   EventRegistrationToken token
);
```

### <a name="parameters"></a>參數

*權杖*<br/>
表示事件處理程式的句柄。 當[Add()](#add)方法註冊事件處理程式時,將返回此令牌。

### <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

### <a name="remarks"></a>備註

有關`EventRegistrationToken`結構的詳細資訊,請參閱**Windows 運行時**參考文檔中的**Windows:基礎::事件註冊權杖結構**主題。

## <a name="eventsourcetargets_"></a><a name="targets"></a>活動來源::targets_

一個或多個事件處理程式的陣列。

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

### <a name="remarks"></a>備註

當由當前`EventSource`物件表示的事件發生時,將調用事件處理程式。

## <a name="eventsourcetargetspointerlock_"></a><a name="targetspointerlock"></a>活動來源:targetsPointerLock_

同步對內部數據成員的訪問,即使正在添加、刪除或調用`EventSource`此事件處理程式也是如此。

```cpp
Wrappers::SRWLock targetsPointerLock_;
```

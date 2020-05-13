---
title: EventTargetArray 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 9ea8800aa22a6b5cae0b3342cf337786fb53fc76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371484"
---
# <a name="eventtargetarray-class"></a>EventTargetArray 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>備註

表示事件處理程式的陣列。

與[EventSource](eventsource-class.md)物件關聯的事件處理程式存儲在受`EventTargetArray`保護的 數據成員中。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                           | 描述
-------------------------------------------------------------- | -----------------------------------------------------------
[事件目標陣列:事件目標陣列](#eventtargetarray)        | 將 `EventTargetArray` 類別的新執行個體初始化。
[事件目標陣列:*事件目標陣列](#tilde-eventtargetarray) | 取消初始化當前`EventTargetArray`類。

### <a name="public-methods"></a>公用方法

名稱                                  | 描述
------------------------------------- | ---------------------------------------------------------------------------------------
[事件目標陣列::添加尾翼](#addtail) | 將指定的事件處理程式追加到事件處理程序的內部陣列的末尾。
[事件目標陣列::開始](#begin)     | 獲取事件處理程序內部陣列中第一個元素的位址。
[事件目標陣列:結束](#end)         | 獲取事件處理程序內部陣列中最後一個元素的位址。
[事件目標陣列:長度](#length)   | 取得事件處理程式內部陣列中的目前元素數。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`EventTargetArray`

## <a name="requirements"></a>需求

**標題:** 事件.h

**命名空間:** 微軟::WRL::D

## <a name="eventtargetarrayeventtargetarray"></a><a name="tilde-eventtargetarray"></a>事件目標陣列:*事件目標陣列

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>備註

取消初始化當前`EventTargetArray`類。

## <a name="eventtargetarrayaddtail"></a><a name="addtail"></a>事件目標陣列::添加尾翼

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>參數

*元素*<br/>
指向要追加的事件處理程序的指標。

### <a name="remarks"></a>備註

將指定的事件處理程式追加到事件處理程序的內部陣列的末尾。

`AddTail()`打算僅由`EventSource`類在內部使用。

## <a name="eventtargetarraybegin"></a><a name="begin"></a>事件目標陣列::開始

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>傳回值

事件處理程式內部陣列中第一個元素的位址。

### <a name="remarks"></a>備註

獲取事件處理程序內部陣列中第一個元素的位址。

## <a name="eventtargetarrayend"></a><a name="end"></a>事件目標陣列:結束

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>傳回值

事件處理程式內部數組中最後一個元素的位址。

### <a name="remarks"></a>備註

獲取事件處理程序內部陣列中最後一個元素的位址。

## <a name="eventtargetarrayeventtargetarray"></a><a name="eventtargetarray"></a>事件目標陣列:事件目標陣列

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>參數

*人力資源*<br/>
在此建構函數操作後,參數*hr*指示陣列的分配是成功還是失敗。 下面的清單顯示了*hr*的可能值。

- S_OK<br/>
  作業成功。

- E_OUTOFMEMORY<br/>
  無法為陣列分配記憶體。

- S_FALSE<br/>
  參數*項*小於或等於零。

*專案*<br/>
要分配的陣列元素的數量。

### <a name="remarks"></a>備註

將 `EventTargetArray` 類別的新執行個體初始化。

`EventTargetArray`用於在`EventSource`物件中保留事件處理程式陣列。

## <a name="eventtargetarraylength"></a><a name="length"></a>事件目標陣列:長度

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
size_t Length();
```

### <a name="return-value"></a>傳回值

事件處理程式的內部數組中的當前元素數。

### <a name="remarks"></a>備註

取得事件處理程式內部陣列中的目前元素數。

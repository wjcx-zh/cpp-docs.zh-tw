---
title: EventTargetArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a02c571f33378ed65fc4b0c4efc7d1a82144279f
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234696"
---
# <a name="eventtargetarray-class"></a>EventTargetArray 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;
```

## <a name="remarks"></a>備註

表示事件處理常式的陣列。

相關聯的事件處理常式[EventSource](../windows/eventsource-class.md)物件會儲存在受保護`EventTargetArray`資料成員。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                           | 描述
-------------------------------------------------------------- | -----------------------------------------------------------
[Eventtargetarray:: Eventtargetarray](#eventtargetarray)        | 初始化 `EventTargetArray` 類別的新執行個體。
[EventTargetArray:: ~ EventTargetArray](#tilde-eventtargetarray) | 取消初始化目前`EventTargetArray`類別。

### <a name="public-methods"></a>公用方法

名稱                                  | 描述
------------------------------------- | ---------------------------------------------------------------------------------------
[Eventtargetarray:: Addtail](#addtail) | 將指定的事件處理常式附加至事件處理常式內部陣列的結尾。
[Eventtargetarray:: Begin](#begin)     | 取得內部陣列中的事件處理常式的第一個元素的位址。
[Eventtargetarray:: End](#end)         | 取得內部陣列中的事件處理常式的最後一個元素的位址。
[Eventtargetarray:: Length](#length)   | 取得目前的元素數目內部陣列中的事件處理常式。

## <a name="inheritance-hierarchy"></a>繼承階層

`EventTargetArray`

## <a name="requirements"></a>需求

**標頭：** event.h

**命名空間：** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray:: ~ EventTargetArray

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>備註

取消初始化目前`EventTargetArray`類別。

## <a name="addtail"></a>Eventtargetarray:: Addtail

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>參數

*項目*<br/>
要附加的事件處理常式的指標。

### <a name="remarks"></a>備註

將指定的事件處理常式附加至事件處理常式內部陣列的結尾。

`AddTail()` 要只可用於在內部`EventSource`類別。

## <a name="begin"></a>Eventtargetarray:: Begin

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>傳回值

內部陣列中的事件處理常式的第一個元素的位址。

### <a name="remarks"></a>備註

取得內部陣列中的事件處理常式的第一個元素的位址。

## <a name="end"></a>Eventtargetarray:: End

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>傳回值

內部陣列中的事件處理常式的最後一個項目位址。

### <a name="remarks"></a>備註

取得內部陣列中的事件處理常式的最後一個元素的位址。

## <a name="eventtargetarray"></a>Eventtargetarray:: Eventtargetarray

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>參數

*hr*<br/>
這個建構函式作業之後，參數*hr*表示配置陣列的成功或失敗。 下列清單顯示可能的值為*hr*。

+   S_OK<br/>
    作業成功。

+   E_OUTOFMEMORY<br/>
    無法配置陣列的記憶體。

+   S_FALSE<br/>
    參數*項目*小於或等於零。

*項目*<br/>
若要配置的陣列元素數目。

### <a name="remarks"></a>備註

初始化 `EventTargetArray` 類別的新執行個體。

`EventTargetArray` 用來保留陣列中的事件處理常式`EventSource`物件。

## <a name="length"></a>Eventtargetarray:: Length

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
size_t Length();
```

### <a name="return-value"></a>傳回值

目前的內部陣列中的事件處理常式的元素數目。

### <a name="remarks"></a>備註

取得目前的元素數目內部陣列中的事件處理常式。

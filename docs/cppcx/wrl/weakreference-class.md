---
title: WeakReference 類別
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a3372a176a158dd9c89eb888c8deb0244eef9a84
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784733"
---
# <a name="weakreference-class"></a>WeakReference 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class WeakReference;
```

## <a name="remarks"></a>備註

代表*弱式參考*可用於使用 Windows 執行階段或傳統 com 使用。 弱式參考代表不一定可存取的物件。

A`WeakReference`物件會維護*強式參考*，這是物件的指標和*強式參考計數*，這是已藉由散發的強式參考的份數`Resolve()`方法。 強式參考計數為非零值，而強式參考有效，且該物件是可存取。 當強式參考計數變成零時，強式參考無效，而且該物件是無法存取。

A`WeakReference`物件一般用來代表其存在由外部執行緒或應用程式所控制的物件。 例如，建構`WeakReference`檔案物件的參考物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

`WeakReference`方法都是安全執行緒。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 描述
----------------------------------------------------- | ---------------------------------------------------------------------------
[Weakreference:: Weakreference](#weakreference)        | 初始化 `WeakReference` 類別的新執行個體。
[WeakReference:: ~ WeakReference](#tilde-weakreference) | 取消初始化 （終結） 的目前執行個體`WeakReference`類別。

### <a name="public-methods"></a>公用方法

名稱                                                                 | 描述
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | 目前的強式的參考計數的遞減`WeakReference`物件。
[WeakReference::IncrementStrongReference](#incrementstrongreference) | 目前的強式參考計數遞增`WeakReference`物件。
[WeakReference::Resolve](#resolve)                                   | 如果強式參考計數為非零值，請為目前的強式參考值設定指定的指標。
[WeakReference::SetUnknown](#setunknown)                             | 設定目前的強式參考`WeakReference`物件與指定的介面指標。

## <a name="inheritance-hierarchy"></a>繼承階層

`WeakReference`

## <a name="requirements"></a>需求

**標頭：** implements.h

**命名空間：** Microsoft::WRL::Details

## <a name="tilde-weakreference"></a>WeakReference:: ~ WeakReference

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

取消初始化目前的執行個體`WeakReference`類別。

## <a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>備註

目前的強式的參考計數的遞減`WeakReference`物件。

當強式參考計數變成零時，強式參考會設定為`nullptr`。

### <a name="return-value"></a>傳回值

遞減的強式參考計數。

## <a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>傳回值

遞增的強式參考計數。

### <a name="remarks"></a>備註

目前的強式參考計數遞增`WeakReference`物件。

## <a name="resolve"></a>WeakReference::Resolve

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>參數

*riid*<br/>
介面識別碼。

*ppvObject*<br/>
這項作業完成時，一份目前的強式參考，如果強式參考計數為非零值。

### <a name="return-value"></a>傳回值

- 如果這項作業會成功，為 S_OK 和強式參考計數為零。 *PpvObject*參數設為`nullptr`。

- 如果這項作業會成功，為 S_OK 和強式參考計數為非零值。 *PpvObject*參數設為強式參考。

- 否則，指出原因的 HRESULT 這項作業失敗。

### <a name="remarks"></a>備註

如果強式參考計數為非零值，請為目前的強式參考值設定指定的指標。

## <a name="setunknown"></a>Weakreference:: Setunknown

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>參數

*unk*<br/>
指標`IUnknown`物件的介面。

### <a name="remarks"></a>備註

設定目前的強式參考`WeakReference`物件與指定的介面指標。

## <a name="weakreference"></a>Weakreference:: Weakreference

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>備註

初始化 `WeakReference` 類別的新執行個體。

強式參考指標`WeakReference`物件會初始化為`nullptr`，和強式參考計數會初始化為 1。

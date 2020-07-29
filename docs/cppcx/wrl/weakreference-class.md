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
ms.openlocfilehash: 9a367a61a029abe1be599b1e262e279402149ccd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220453"
---
# <a name="weakreference-class"></a>WeakReference 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
class WeakReference;
```

## <a name="remarks"></a>備註

表示可以搭配 Windows 執行階段或傳統 COM 使用的*弱式參考*。 弱式參考代表不一定可存取的物件。

`WeakReference`物件會維護*強式參考*，也就是物件的指標，以及強式*參考計數*，這是方法已散發之強式參考的複本數目 `Resolve()` 。 雖然強式參考計數是非零值，但強式參考是有效的，而且物件是可存取的。 當強式參考計數變成零時，強式參考會無效，而且無法存取物件。

`WeakReference`物件通常用來表示物件，其存在是由外部執行緒或應用程式所控制。 例如， `WeakReference` 從檔案物件的參考來建立物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

這些 `WeakReference` 方法都是安全線程。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 說明
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference：： WeakReference](#weakreference)        | 初始化 `WeakReference` 類別的新執行個體。
[WeakReference：： ~ WeakReference](#tilde-weakreference) | 將（損毀）類別的目前實例 `WeakReference` 。

### <a name="public-methods"></a>公用方法

名稱                                                                 | 說明
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference：:D ecrementStrongReference](#decrementstrongreference) | 遞減目前物件的強式參考計數 `WeakReference` 。
[WeakReference：： IncrementStrongReference](#incrementstrongreference) | 遞增目前物件的強式參考計數 `WeakReference` 。
[WeakReference：： Resolve](#resolve)                                   | 如果強式參考計數不是零，則將指定的指標設定為目前的強式參考值。
[WeakReference：： SetUnknown](#setunknown)                             | 將目前物件的強式參考設定 `WeakReference` 為指定的介面指標。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WeakReference`

## <a name="requirements"></a>需求

**標頭：** implements。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference：： ~ WeakReference

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

將類別的目前實例 `WeakReference` 。

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference：:D ecrementStrongReference

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>備註

遞減目前物件的強式參考計數 `WeakReference` 。

當強式參考計數變成零時，強式參考會設定為 **`nullptr`** 。

### <a name="return-value"></a>傳回值

遞減的強式參考計數。

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference：： IncrementStrongReference

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>傳回值

遞增的強式參考計數。

### <a name="remarks"></a>備註

遞增目前物件的強式參考計數 `WeakReference` 。

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference：： Resolve

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

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
當此作業完成時，如果強式參考計數不是零，則為目前強式參考的複本。

### <a name="return-value"></a>傳回值

- 如果此作業成功且強式參考計數為零，則 S_OK。 *PpvObject*參數會設定為 **`nullptr`** 。

- S_OK 此作業是否成功，且強式參考計數不是零。 *PpvObject*參數會設定為強式參考。

- 否則，即為 HRESULT，表示此作業失敗的原因。

### <a name="remarks"></a>備註

如果強式參考計數不是零，則將指定的指標設定為目前的強式參考值。

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference：： SetUnknown

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>參數

*unk*<br/>
`IUnknown`物件介面的指標。

### <a name="remarks"></a>備註

將目前物件的強式參考設定 `WeakReference` 為指定的介面指標。

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference：： WeakReference

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>備註

初始化 `WeakReference` 類別的新執行個體。

物件的強式參考指標 `WeakReference` 會初始化為 **`nullptr`** ，而強式參考計數會初始化為1。

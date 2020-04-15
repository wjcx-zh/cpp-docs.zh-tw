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
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374211"
---
# <a name="weakreference-class"></a>WeakReference 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
class WeakReference;
```

## <a name="remarks"></a>備註

表示可與 Windows 執行時或經典 COM 一起使用*的弱參考*。 弱式參考代表不一定可存取的物件。

物件維護*強引用*,它是指向物件的指標和*強引用計數*,即`Resolve()`該方法 分發的強引用的副`WeakReference`本數。 雖然強引用計數是非零的,但強引用是有效的,並且對像是可訪問的。 當強引用計數變為零時,強引用無效,並且物件不可訪問。

物件`WeakReference`通常用於表示其存在由外部線程或應用程式控制的物件。 例如,從對檔`WeakReference`物件的引用構造物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。

這些方法`WeakReference`是線程安全的。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                                                  | 描述
----------------------------------------------------- | ---------------------------------------------------------------------------
[弱參考::弱參考](#weakreference)        | 將 `WeakReference` 類別的新執行個體初始化。
[弱參考:*弱參考](#tilde-weakreference) | 取消初始化(銷毀)`WeakReference`類的當前實例。

### <a name="public-methods"></a>公用方法

名稱                                                                 | 描述
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[弱參考::D強參考](#decrementstrongreference) | 聲明當前`WeakReference`物件的強引用計數。
[弱參考::增量強參考](#incrementstrongreference) | 增加當前`WeakReference`對象的強引用計數。
[弱參考::解決](#resolve)                                   | 如果強引用計數為非零,則設置指向當前強引用值的指定指標。
[弱參考::設定未知](#setunknown)                             | 將當前`WeakReference`物件的強引用設置到指定的介面指標。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`WeakReference`

## <a name="requirements"></a>需求

**標題:** 實現.h

**命名空間:** 微軟::WRL::D

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>弱參考:*弱參考

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

取消初始化類的`WeakReference`當前實例。

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>弱參考::D強參考

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>備註

聲明當前`WeakReference`物件的強引用計數。

當強引用計數變為零時,強引用設定為`nullptr`。

### <a name="return-value"></a>傳回值

遞減的強引用計數。

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>弱參考::增量強參考

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>傳回值

遞增的強引用計數。

### <a name="remarks"></a>備註

增加當前`WeakReference`對象的強引用計數。

## <a name="weakreferenceresolve"></a><a name="resolve"></a>弱參考::解決

支援 WRL 基礎結構,不打算直接從代碼中使用。

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
此操作完成後,如果強引用計數為非零,則當前強引用的副本。

### <a name="return-value"></a>傳回值

- 如果此操作成功且強引用計數為零,S_OK。 *ppvObject*參數設定`nullptr`為 。

- 如果此操作成功且強引用計數為非零,則S_OK。 *ppvObject*參數設定為強引用。

- 否則,指示此操作失敗原因的 HRESULT。

### <a name="remarks"></a>備註

如果強引用計數為非零,則設置指向當前強引用值的指定指標。

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>弱參考::設定未知

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>參數

*unk*<br/>
指向物件`IUnknown`介面的指標。

### <a name="remarks"></a>備註

將當前`WeakReference`物件的強引用設置到指定的介面指標。

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>弱參考::弱參考

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
WeakReference();
```

### <a name="remarks"></a>備註

將 `WeakReference` 類別的新執行個體初始化。

`WeakReference`物件的強引用指標初始化到`nullptr`,強引用計數初始化為 1。

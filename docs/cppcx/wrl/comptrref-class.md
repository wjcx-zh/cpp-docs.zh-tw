---
title: ComPtrRef 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
- client/Microsoft::WRL::Details::ComPtrRef::operator==
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
- client/Microsoft::WRL::Details::ComPtrRef::operator InterfaceType**
- client/Microsoft::WRL::Details::ComPtrRef::operator*
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
- client/Microsoft::WRL::Details::ComPtrRef::operator void**
- client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRef class
- Microsoft::WRL::Details::ComPtrRef::ComPtrRef, constructor
- Microsoft::WRL::Details::ComPtrRef::GetAddressOf method
- Microsoft::WRL::Details::ComPtrRef::operator== operator
- Microsoft::WRL::Details::ComPtrRef::operator!= operator
- Microsoft::WRL::Details::ComPtrRef::operator InterfaceType** operator
- Microsoft::WRL::Details::ComPtrRef::operator* operator
- Microsoft::WRL::Details::ComPtrRef::operator T* operator
- Microsoft::WRL::Details::ComPtrRef::operator void** operator
- Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf method
ms.assetid: d6bdfd20-e977-45b4-9ac1-1b8efbdb77de
ms.openlocfilehash: f92a3e14018cf8c02dec40b664b72a0956f6220e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220531"
---
# <a name="comptrref-class"></a>ComPtrRef 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>參數

*T*<br/>
[ComPtr \<T> ](comptr-class.md)類型或衍生自它的類型，而不只是所表示的介面 `ComPtr` 。

## <a name="remarks"></a>備註

表示類型物件的參考 `ComPtr<T>` 。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 說明
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef：： ComPtrRef](#comptrref) | `ComPtrRef`從另一個物件的指定指標，初始化類別的新實例 `ComPtrRef` 。

### <a name="public-methods"></a>公用方法

名稱                                                         | 說明
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：： GetAddressOf](#getaddressof)                     | 抓取目前物件所代表之介面的指標位址 `ComPtrRef` 。
[ComPtrRef：： ReleaseAndGetAddressOf](#releaseandgetaddressof) | 刪除目前的 `ComPtrRef` 物件，並傳回物件所代表之介面的指標指向指標 `ComPtrRef` 。

### <a name="public-operators"></a>公用運算子

名稱                                                                     | 說明
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef：： operator InterfaceType * *](#operator-interfacetype-star-star) | 刪除目前的 `ComPtrRef` 物件，並傳回物件所代表之介面的指標指向指標 `ComPtrRef` 。
[ComPtrRef：： operator T *](#operator-t-star)                               | 傳回目前 ComPtrRef 物件之[ptr_](comptrrefbase-class.md#ptr)資料成員的值。
[ComPtrRef：： operator void * *](#operator-void-star-star)                   | 刪除目前的 `ComPtrRef` 物件，將物件所表示之介面的指標，轉換為指標指標，然後傳回 `ComPtrRef` **`void`** 轉換指標。
[ComPtrRef：： operator *](#operator-star)                                   | 抓取目前物件所代表之介面的指標 `ComPtrRef` 。
[ComPtrRef：： operator = =](#operator-equality)                              | 表示兩個 `ComPtrRef` 物件是否相等。
[ComPtrRef：： operator！ =](#operator-inequality)                            | 表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef：： ComPtrRef

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>參數

*ptr*<br/>
另一個物件的基礎值 `ComPtrRef` 。

### <a name="remarks"></a>備註

`ComPtrRef`從另一個物件的指定指標，初始化類別的新實例 `ComPtrRef` 。

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef：： GetAddressOf

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>傳回值

目前物件所代表之介面的指標位址 `ComPtrRef` 。

### <a name="remarks"></a>備註

抓取目前物件所代表之介面的指標位址 `ComPtrRef` 。

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef：： operator = =

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>參數

*為*<br/>
`ComPtrRef` 物件的參考。

*位元組*<br/>
另一個物件的參考 `ComPtrRef` ，或匿名型別的指標（ **`void*`** ）。

### <a name="return-value"></a>傳回值

**`true`** 如果物件*a*等於物件*b*，第一個運算子會產生，否則為 **`false`** 。

第二個和第三個運算子會產生， **`true`** 如果物件*a*等於 **`nullptr`** ，則為，否則為 **`false`** 。

第四個和第五個運算子 **`true`** 會產生（如果物件*a*等於物件*b*），否則為 **`false`** 。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否相等。

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef：： operator！ =

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>參數

*為*<br/>
`ComPtrRef` 物件的參考。

*位元組*<br/>
另一個物件的參考 `ComPtrRef` ，或匿名物件的指標（ **`void*`** ）。

### <a name="return-value"></a>傳回值

**`true`** 如果物件*a*不等於物件*b*，第一個運算子會產生，否則為 **`false`** 。

第二個和第三個運算子 **`true`** 會產生，如果物件*a*不等於，則為 **`nullptr`** ，否則為 **`false`** 。

第四個和第五個運算子 **`true`** 會產生（如果物件*a*不等於物件*b*），否則為 **`false`** 。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef：： operator InterfaceType\*\*

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>備註

刪除目前的 `ComPtrRef` 物件，並傳回物件所代表之介面的指標指向指標 `ComPtrRef` 。

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef：： operator *

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>傳回值

目前物件所代表之介面的指標 `ComPtrRef` 。

### <a name="remarks"></a>備註

抓取目前物件所代表之介面的指標 `ComPtrRef` 。

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef：： operator T *

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
operator T*();
```

### <a name="remarks"></a>備註

傳回目前物件之[ptr_](comptrrefbase-class.md#ptr)資料成員的值 `ComPtrRef` 。

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef：： operator void\*\*

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>備註

刪除目前的 `ComPtrRef` 物件，將物件所表示之介面的指標，轉換為指標指標，然後傳回 `ComPtrRef` **`void`** 轉換指標。

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtrRef：： ReleaseAndGetAddressOf

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

已刪除之物件所表示之介面的指標 `ComPtrRef` 。

### <a name="remarks"></a>備註

刪除目前的 `ComPtrRef` 物件，並傳回物件所代表之介面的指標指向指標 `ComPtrRef` 。

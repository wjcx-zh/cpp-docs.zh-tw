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
ms.openlocfilehash: df9ded817227547493c04035e0abc3d948e24495
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372627"
---
# <a name="comptrref-class"></a>ComPtrRef 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>參數

*T*<br/>
[ComPtr\<T>](comptr-class.md)類型或從它派生的類型,而不僅僅是`ComPtr`由 表示的介面。

## <a name="remarks"></a>備註

表示對類型`ComPtr<T>`物件的引用。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[ComPtrRef:ComPtrRef](#comptrref) | 從指定的指標初始化`ComPtrRef`類的新實例到另一個`ComPtrRef`物件。

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef:取得位址](#getaddressof)                     | 檢索指向當前`ComPtrRef`物件表示的介面的指標的位址。
[Comptrref::發佈和取得位址](#releaseandgetaddressof) | 刪除當前`ComPtrRef`物件,並返回指向物件表示的介面`ComPtrRef`的指標指向指標。

### <a name="public-operators"></a>公用運算子

名稱                                                                     | 描述
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtrRef::操作員介面類型*](#operator-interfacetype-star-star) | 刪除當前`ComPtrRef`物件,並返回指向物件表示的介面`ComPtrRef`的指標指向指標。
[ComPtrRef::運算子 T*](#operator-t-star)                               | 傳回目前的 ComPtrRef 物件的[ptr_](comptrrefbase-class.md#ptr)資料成員的值。
[ComPtrRef::操作員空隙*](#operator-void-star-star)                   | 刪除當前`ComPtrRef`物件,將`ComPtrRef`指向 該物件表示的介面的指標轉換為指標到`void`指標到,然後返回強制轉換指標。
[ComPtrRef:管理員*](#operator-star)                                   | 檢索指向當前`ComPtrRef`物件表示的介面的指標。
[ComPtrRef::運算符 *](#operator-equality)                              | 表示兩個 `ComPtrRef` 物件是否相等。
[ComPtrRef:操作員!](#operator-inequality)                            | 表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間:** 微軟::WRL::D

## <a name="comptrrefcomptrref"></a><a name="comptrref"></a>ComPtrRef:ComPtrRef

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>參數

*Ptr*<br/>
另一個`ComPtrRef`物件的基礎值。

### <a name="remarks"></a>備註

從指定的指標初始化`ComPtrRef`類的新實例到另一個`ComPtrRef`物件。

## <a name="comptrrefgetaddressof"></a><a name="getaddressof"></a>ComPtrRef:取得位址

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>傳回值

指向當前`ComPtrRef`物件表示的介面的指標的位址。

### <a name="remarks"></a>備註

檢索指向當前`ComPtrRef`物件表示的介面的指標的位址。

## <a name="comptrrefoperator"></a><a name="operator-equality"></a>ComPtrRef::運算符 *

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*a*<br/>
`ComPtrRef` 物件的參考。

*B*<br/>
另一個`ComPtrRef`物件的參考,或指向匿名類型的指標 (`void*`。

### <a name="return-value"></a>傳回值

如果物件*a*等於物件*b,* 則第一個運算符將生成**為 true。** 否則,**假**。

**如果物件** *a*等於**nullptr,** 則第二個和第三個運算元將 true。否則,**假**。

**如果物件**a 等於物件*b,* 則*b*第四和第 五運算元將 true;否則,**假**。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否相等。

## <a name="comptrrefoperator"></a><a name="operator-inequality"></a>ComPtrRef:操作員!

支援 WRL 基礎結構,不打算直接從代碼中使用。

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

*a*<br/>
`ComPtrRef` 物件的參考。

*B*<br/>
另一`ComPtrRef`個物件的參考或指向匿名物件的指標 (`void*`。

### <a name="return-value"></a>傳回值

如果物件 a 不等於物件*b,* 則第*b*一個運算符將生成**為 true。** 否則,**假**。

**如果物件** *a*不等於**nullptr,** 則第二個和第三個運算符將 true。否則,**假**。

**如果物件**a 不等於物件*b,* 則*b*第四和第 五運算符將 true。否則,**假**。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="comptrrefoperator-interfacetype"></a><a name="operator-interfacetype-star-star"></a>ComPtrRef::操作員介面類型*

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>備註

刪除當前`ComPtrRef`物件,並返回指向物件表示的介面`ComPtrRef`的指標指向指標。

## <a name="comptrrefoperator"></a><a name="operator-star"></a>ComPtrRef:管理員*

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>傳回值

指向當前`ComPtrRef`物件表示的介面的指標。

### <a name="remarks"></a>備註

檢索指向當前`ComPtrRef`物件表示的介面的指標。

## <a name="comptrrefoperator-t"></a><a name="operator-t-star"></a>ComPtrRef::運算子 T*

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
operator T*();
```

### <a name="remarks"></a>備註

返回當前`ComPtrRef`物件的[ptr_](comptrrefbase-class.md#ptr)數據成員的值。

## <a name="comptrrefoperator-void"></a><a name="operator-void-star-star"></a>ComPtrRef::操作員空隙\*\*

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>備註

刪除當前`ComPtrRef`物件,將`ComPtrRef`指向 該物件表示的介面的指標轉換為指標到`void`指標到,然後返回強制轉換指標。

## <a name="comptrrefreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>Comptrref::發佈和取得位址

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

指向已刪除`ComPtrRef`物件表示的介面的指標。

### <a name="remarks"></a>備註

刪除當前`ComPtrRef`物件,並返回指向物件表示的介面`ComPtrRef`的指標指向指標。

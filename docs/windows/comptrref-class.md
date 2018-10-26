---
title: ComPtrRef 類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3902bcb43b1aa02f6d5ec66b919a2685dccccd99
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070305"
---
# <a name="comptrref-class"></a>ComPtrRef 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRef : public ComPtrRefBase<T>;
```

### <a name="parameters"></a>參數

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md)型別或型別衍生它，不只是將所代表之介面`ComPtr`。

## <a name="remarks"></a>備註

表示型別的物件的參考`ComPtr<T>`。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

名稱                               | 描述
---------------------------------- | -------------------------------------------------------------------------------------------------------------
[Comptrref:: Comptrref](#comptrref) | 初始化的新執行個體`ComPtrRef`到另一個指定的指標類別`ComPtrRef`物件。

### <a name="public-methods"></a>公用方法

名稱                                                         | 描述
------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: Getaddressof](#getaddressof)                     | 擷取目前所代表之介面的指標位址`ComPtrRef`物件。
[Comptrref:: Releaseandgetaddressof](#releaseandgetaddressof) | 刪除目前`ComPtrRef`物件，並傳回已所代表之介面的指標-到-a-指標`ComPtrRef`物件。

### <a name="public-operators"></a>公用運算子

名稱                                                                     | 描述
------------------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptrref:: Operator InterfaceType * *](#operator-interfacetype-star-star) | 刪除目前`ComPtrRef`物件，並傳回已所代表之介面的指標-到-a-指標`ComPtrRef`物件。
[Comptrref:: Operator T *](#operator-t-star)                               | 傳回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)目前的 ComPtrRef 物件資料成員。
[Comptrref:: Operator void * *](#operator-void-star-star)                   | 刪除目前`ComPtrRef`物件，轉換已由介面指標`ComPtrRef`物件做為指標至-指標-對`void`，然後傳回型別轉換指標。
[Comptrref:: Operator *](#operator-star)                                   | 擷取目前所代表之介面指標`ComPtrRef`物件。
[Comptrref:: Operator = =](#operator-equality)                              | 表示兩個 `ComPtrRef` 物件是否相等。
[Comptrref:: Operator ！ =](#operator-inequality)                            | 表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtrRefBase`

`ComPtrRef`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="comptrref"></a>Comptrref:: Comptrref

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
ComPtrRef(
   _In_opt_ T* ptr
);
```

### <a name="parameters"></a>參數

*ptr*<br/>
另一個的基礎值`ComPtrRef`物件。

### <a name="remarks"></a>備註

初始化的新執行個體`ComPtrRef`到另一個指定的指標類別`ComPtrRef`物件。

## <a name="getaddressof"></a>Comptrref:: Getaddressof

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
InterfaceType* const * GetAddressOf() const;
```

### <a name="return-value"></a>傳回值

代表由目前之介面的指標位址`ComPtrRef`物件。

### <a name="remarks"></a>備註

擷取目前所代表之介面的指標位址`ComPtrRef`物件。

## <a name="operator-equality"></a>Comptrref:: Operator = =

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
對 `ComPtrRef` 物件的參考。

*b*<br/>
另一個的參考`ComPtrRef`物件或匿名類型的指標 (`void*`)。

### <a name="return-value"></a>傳回值

第一個運算子會產生 **，則為 true**如果物件是否等於物件*b*否則**false**。

第二個和第三個運算子會產生 **，則為 true**如果物件等於**nullptr**，則為**false**。

第四個和第五個運算子會產生 **，則為 true**如果物件是否等於物件*b*，則為**false**。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否相等。

## <a name="operator-inequality"></a>Comptrref:: Operator ！ =

支援 WRL 結構，而且不是直接從您的程式碼使用。

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
對 `ComPtrRef` 物件的參考。

*b*<br/>
另一個的參考`ComPtrRef`物件或匿名物件的指標 (`void*`)。

### <a name="return-value"></a>傳回值

第一個運算子會產生 **，則為 true**如果物件是否不等於物件*b*否則**false**。

第二個和第三個運算子會產生 **，則為 true**如果物件是否不等於**nullptr**，則為**false**。

第四個和第五個運算子會產生 **，則為 true**如果物件是否不等於物件*b*，則為**false**。

### <a name="remarks"></a>備註

表示兩個 `ComPtrRef` 物件是否不相等。

## <a name="operator-interfacetype-star-star"></a>Comptrref:: Operator InterfaceType * *

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
operator InterfaceType**();
```

### <a name="remarks"></a>備註

刪除目前`ComPtrRef`物件，並傳回已所代表之介面的指標-到-a-指標`ComPtrRef`物件。

## <a name="operator-star"></a>Comptrref:: Operator *

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
InterfaceType* operator *();
```

### <a name="return-value"></a>傳回值

目前所代表之介面指標`ComPtrRef`物件。

### <a name="remarks"></a>備註

擷取目前所代表之介面指標`ComPtrRef`物件。

## <a name="operator-t-star"></a>Comptrref:: Operator T *

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
operator T*();
```

### <a name="remarks"></a>備註

傳回的值[ptr_](../windows/comptrrefbase-ptr-data-member.md)目前的資料成員`ComPtrRef`物件。

## <a name="operator-void-star-star"></a>Comptrref:: Operator void\*\*

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
operator void**() const;
```

### <a name="remarks"></a>備註

刪除目前`ComPtrRef`物件，轉換已由介面指標`ComPtrRef`物件做為指標至-指標-對`void`，然後傳回型別轉換指標。

## <a name="releaseandgetaddressof"></a>Comptrref:: Releaseandgetaddressof

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
InterfaceType** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>傳回值

已呈現之介面指標的已刪除`ComPtrRef`物件。

### <a name="remarks"></a>備註

刪除目前`ComPtrRef`物件，並傳回已所代表之介面的指標-到-a-指標`ComPtrRef`物件。

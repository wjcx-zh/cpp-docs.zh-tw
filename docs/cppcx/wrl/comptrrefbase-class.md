---
title: ComPtrRefBase 類別
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398637"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 類別

支援 WRL 結構，而且不是直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>參數

*T*<br/>
A [ComPtr\<T >](comptr-class.md)型別或型別衍生它，不只是將所代表之介面`ComPtr`。

## <a name="remarks"></a>備註

表示基底類別[ComPtrRef](comptrref-class.md)類別。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | -------------------------------------------------
`InterfaceType` | 範本參數類型的同義字*T*。

### <a name="public-operators"></a>公用運算子

名稱                                                                       | 描述
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[Comptrrefbase:: Operator IInspectable * *](#operator-iinspectable-star-star) | 將目前的轉換[ptr_](#ptr)資料成員指標至-a-指標-對`IInspectable`介面。
[Comptrrefbase:: Operator IUnknown * *](#operator-iunknown-star-star)         | 將目前的轉換[ptr_](#ptr)資料成員指標至-a-指標-對`IUnknown`介面。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | 目前的範本參數所指定之類型的指標。

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtrRefBase`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL::Details

## <a name="operator-iinspectable-star-star"></a>Comptrrefbase:: Operator IInspectable\* \*運算子

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>備註

將目前的轉換[ptr_](#ptr)資料成員指標至-a-指標-對`IInspectable`介面。

會發出錯誤，如果目前`ComPtrRefBase`不是衍生自`IInspectable`。

這項轉換可才`__WRL_CLASSIC_COM__`定義。

## <a name="operator-iunknown-star-star"></a>Comptrrefbase:: Operator IUnknown * * 運算子

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>備註

將目前的轉換[ptr_](#ptr)資料成員指標至-a-指標-對`IUnknown`介面。

會發出錯誤，如果目前`ComPtrRefBase`不是衍生自`IUnknown`。

## <a name="ptr"></a>ComPtrRefBase::ptr_

支援 WRL 結構，而且不是直接從您的程式碼使用。

```cpp
T* ptr_;
```

### <a name="remarks"></a>備註

目前的範本參數所指定之類型的指標。 `ptr_` 是受保護的資料成員。

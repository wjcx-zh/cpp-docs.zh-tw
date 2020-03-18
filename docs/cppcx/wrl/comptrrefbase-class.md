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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418311"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 類別

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>參數

*T*<br/>
[ComPtr\<t >](comptr-class.md)類型或從中衍生的類型，而不只是 `ComPtr`所表示的介面。

## <a name="remarks"></a>備註

表示[ComPtrRef](comptrref-class.md)類別的基類。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | -------------------------------------------------
`InterfaceType` | 樣板參數*T*類型的同義字。

### <a name="public-operators"></a>公用運算子

名稱                                                                       | 描述
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase：： operator IInspectable * *](#operator-iinspectable-star-star) | 將目前的[ptr_](#ptr)資料成員轉換成指向 `IInspectable` 介面的指標。
[ComPtrRefBase：： operator IUnknown * *](#operator-iunknown-star-star)         | 將目前的[ptr_](#ptr)資料成員轉換成指向 `IUnknown` 介面的指標。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase：:p tr_](#ptr) | 目前範本參數所指定之類型的指標。

## <a name="inheritance-hierarchy"></a>繼承階層

`ComPtrRefBase`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase：： operator IInspectable\*\* 運算子

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>備註

將目前的[ptr_](#ptr)資料成員轉換成指向 `IInspectable` 介面的指標。

如果目前的 `ComPtrRefBase` 不是衍生自 `IInspectable`，就會發出錯誤。

只有在已定義 `__WRL_CLASSIC_COM__` 時，才可以使用這個轉換。

## <a name="operator-iunknown-star-star"></a>ComPtrRefBase：： operator IUnknown * * 運算子

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>備註

將目前的[ptr_](#ptr)資料成員轉換成指向 `IUnknown` 介面的指標。

如果目前的 `ComPtrRefBase` 不是衍生自 `IUnknown`，就會發出錯誤。

## <a name="ptr"></a>ComPtrRefBase：:p tr_

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

```cpp
T* ptr_;
```

### <a name="remarks"></a>備註

目前範本參數所指定之類型的指標。 `ptr_` 是受保護的資料成員。

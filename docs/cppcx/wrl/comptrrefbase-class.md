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
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372623"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase 類別

支援 WRL 基礎結構,不打算直接從代碼中使用。

## <a name="syntax"></a>語法

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>參數

*T*<br/>
[ComPtr\<T>](comptr-class.md)類型或從它派生的類型,而不僅僅是`ComPtr`由 表示的介面。

## <a name="remarks"></a>備註

表示[ComPtrRef](comptrref-class.md)類的基類。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

名稱            | 描述
--------------- | -------------------------------------------------
`InterfaceType` | 範本參數*T*類型的同義詞。

### <a name="public-operators"></a>公用運算子

名稱                                                                       | 描述
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::操作員可檢測*](#operator-iinspectable-star-star) | 將當前[ptr_](#ptr)資料成員轉換為指向`IInspectable`介面的指標。
[ComPtrRefBase::操作員I未知*](#operator-iunknown-star-star)         | 將當前[ptr_](#ptr)資料成員轉換為指向`IUnknown`介面的指標。

### <a name="protected-data-members"></a>受保護的資料成員

名稱                        | 描述
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr]](#ptr) | 指向當前範本參數指定的類型。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ComPtrRefBase`

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間:** 微軟::WRL::D

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase::管理員可檢查\*\*操作員

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>備註

將當前[ptr_](#ptr)資料成員轉換為指向`IInspectable`介面的指標。

如果電流`ComPtrRefBase`未派生`IInspectable`自 ,則將發出錯誤。

此強制轉換僅在定義時`__WRL_CLASSIC_COM__`才可用。

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase::管理員 I 未知* 運算子

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>備註

將當前[ptr_](#ptr)資料成員轉換為指向`IUnknown`介面的指標。

如果電流`ComPtrRefBase`未派生`IUnknown`自 ,則將發出錯誤。

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr]

支援 WRL 基礎結構,不打算直接從代碼中使用。

```cpp
T* ptr_;
```

### <a name="remarks"></a>備註

指向當前範本參數指定的類型。 `ptr_`是受保護的數據成員。

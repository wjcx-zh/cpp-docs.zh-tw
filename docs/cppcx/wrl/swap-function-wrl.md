---
title: Swap 函式（WRL）
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: e665dbca025da56ba81c3fdf1749b2d653b78c00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213560"
---
# <a name="swap-function-wrl"></a>Swap 函式（WRL）

支援 WRL 基礎結構，但不適合直接從您的程式碼使用。

## <a name="syntax"></a>語法

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>參數

*left*<br/>
第一個引數。

*right*<br/>
第二個引數。

## <a name="return-value"></a>傳回值

## <a name="remarks"></a>備註

交換兩個指定引數的值。

## <a name="requirements"></a>需求

**標頭：** 內部。h

**命名空間：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Details 命名空間](microsoft-wrl-details-namespace.md)

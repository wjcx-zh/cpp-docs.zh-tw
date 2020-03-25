---
title: _variant_t 關係運算子
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
ms.openlocfilehash: e0d7ea1a0bcaf8329cff0cdfb0c01154f3c5a73b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187566"
---
# <a name="_variant_t-relational-operators"></a>_variant_t 關係運算子

**Microsoft 專屬**

比較兩個 `_variant_t` 物件是否相等或不等。

## <a name="syntax"></a>語法

```
bool operator==(
   const VARIANT& varSrc) const;
bool operator==(
   const VARIANT* pSrc) const;
bool operator!=(
   const VARIANT& varSrc) const;
bool operator!=(
   const VARIANT* pSrc) const;
```

#### <a name="parameters"></a>參數

*varSrc*<br/>
要與 `_variant_t` 物件比較的 `VARIANT`。

*.Psrc*<br/>
要與 `_variant_t` 物件比較之 `VARIANT` 的指標。

## <a name="return-value"></a>傳回值

如果比較保留，則傳回**true** ，否則傳回**false** 。

## <a name="remarks"></a>備註

比較 `_variant_t` 物件與 `VARIANT`，測試是否相等或不相等。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)

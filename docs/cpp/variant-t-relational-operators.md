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
ms.openlocfilehash: 6e0296a2bf4ce97e41fdf6208c3dd1c6b91215dc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226931"
---
# <a name="_variant_t-relational-operators"></a>_variant_t 關係運算子

**Microsoft 特定的**

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
`VARIANT`要與物件比較的 `_variant_t` 。

*.Psrc*<br/>
要 `VARIANT` 與物件比較之的指標 `_variant_t` 。

## <a name="return-value"></a>傳回值

**`true`** 如果比較保留，則傳回， **`false`** 否則傳回。

## <a name="remarks"></a>備註

比較 `_variant_t` 物件與 `VARIANT` ，測試是否相等或不等。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)

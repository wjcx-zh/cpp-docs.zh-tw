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
ms.openlocfilehash: e0d26247868440f47c73422510ac0e998f8e8dee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403291"
---
# <a name="variantt-relational-operators"></a>_variant_t 關係運算子

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
A`VARIANT`要與比較`_variant_t`物件。

*pSrc*<br/>
指標`VARIANT`要與比較`_variant_t`物件。

## <a name="return-value"></a>傳回值

傳回**真**成立，如果**false**如果不是。

## <a name="remarks"></a>備註

比較`_variant_t`物件`VARIANT`、 測試是否相等或不等比較。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_variant_t 類別](../cpp/variant-t-class.md)
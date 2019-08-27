---
title: is_lvalue_reference 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: 5bcd5c8333f011475cb11a452759c8986ab22215
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456209"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference 類別

測試類型是否為 lvalue 參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是物件或函式的參考, 則此類型述詞的實例為 true, 否則為 false。 請注意, *Ty*可能不是右值參考。 如需有關 rvalue 的詳細資訊，請參閱 [Rvalue 參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)

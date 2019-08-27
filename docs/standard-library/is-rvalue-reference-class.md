---
title: is_rvalue_reference 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: 58cbf5709eda4f41d2edab7ddac1e0a04a9c74cf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455675"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 類別

測試類型是否為 rvalue 參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

## <a name="remarks"></a>備註

如果類型*Ty*是[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md), 此類型述詞的實例會保留 true。

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)

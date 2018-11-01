---
title: is_lvalue_reference 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_lvalue_reference
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
ms.openlocfilehash: e032522e790b7027886ba1a6199ed7fdf86c0936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460173"
---
# <a name="islvaluereference-class"></a>is_lvalue_reference 類別

測試類型是否為 lvalue 參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_lvalue_reference;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果這個型別述詞執行個體保留 true 的型別*Ty*物件或函式，否則為 false 的參考。 請注意， *Ty*可能不是右值參考。 如需有關 rvalue 的詳細資訊，請參閱 [Rvalue 參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>

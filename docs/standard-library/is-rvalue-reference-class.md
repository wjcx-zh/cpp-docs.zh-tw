---
title: is_rvalue_reference 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_rvalue_reference
helpviewer_keywords:
- is_rvalue_reference class
- is_rvalue_reference
ms.assetid: 40a97072-7b5c-4274-9154-298d3dcf064a
ms.openlocfilehash: ea3be02db2a4a840ed8f8b8a253d7409c26cf759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604111"
---
# <a name="isrvaluereference-class"></a>is_rvalue_reference 類別

測試類型是否為 rvalue 參考。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_rvalue_reference;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果這個型別述詞執行個體保留 true 的型別*Ty*是[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>

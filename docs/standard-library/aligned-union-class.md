---
title: aligned_union 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: b9ffb4aff4d4d5667ab8d626ea13a21da94ca0c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456469"
---
# <a name="alignedunion-class"></a>aligned_union 類別

提供夠大並適當對齊的 POD 類型來儲存等位類型，以及所需的大小。

## <a name="syntax"></a>語法

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>參數

*Len*\
等位中最大類型的對齊值。

*類型*\
基礎等位中的不同類型。

## <a name="remarks"></a>備註

使用此範本類別，即可取得將等位儲存在未初始化儲存空間中所需的對齊和大小。 成員 typedef `type`會將 POD 類型命名為適用于*類型*中所列任何類型的儲存, 大小下限為*Len*。 類型`alignment_value` 的`std::size_t`靜態成員包含*類型*中所列所有類型所需的最嚴格對齊。

## <a name="example"></a>範例

下列範例示範如何使用 `aligned_union` 配置對齊的堆疊緩衝區來放置等位。

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[alignment_of 類別](../standard-library/alignment-of-class.md)

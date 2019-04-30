---
title: aligned_union 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: 1a26675879c50440a4955989aca178dbe5049fdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411106"
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

*Len*<br/>
等位中最大類型的對齊值。

*型別*<br/>
基礎等位中的不同類型。

## <a name="remarks"></a>備註

使用此範本類別，即可取得將等位儲存在未初始化儲存空間中所需的對齊和大小。 成員 typedef`type`名稱的 POD 類型適用於中所列出的任何類型的儲存體*型別*; 大小下限是*Len*。 靜態成員`alignment_value`型別的`std::size_t`包含中列出的所有類型的所需的最嚴格對齊*型別*。

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

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of 類別](../standard-library/alignment-of-class.md)<br/>

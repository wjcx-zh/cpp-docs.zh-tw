---
title: aligned_union 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::aligned_union
dev_langs:
- C++
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a149269117f83b18838d54c728d6d8da580882b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
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

`Len` 對齊值，此等位中最大的類型。

`Types` 基礎等位中不同的類型。

## <a name="remarks"></a>備註

使用此範本類別，即可取得將等位儲存在未初始化儲存空間中所需的對齊和大小。 成員 typedef `type` 會命名適合儲存 `Types` 中所列之任何類型的 POD 類型；大小下限為 `Len`。 類型 `std::size_t` 的靜態成員 `alignment_value` 包含 `Types` 中所列之所有類型需要的最嚴格對齊。

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

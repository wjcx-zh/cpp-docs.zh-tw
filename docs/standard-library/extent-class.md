---
title: extent 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 0cd53ba8537e706a68ffdcf08df998108266ad20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457785"
---
# <a name="extent-class"></a>extent 類別

取得陣列維度。

## <a name="syntax"></a>語法

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

*怎樣*\
要查詢的陣列界限

## <a name="remarks"></a>備註

如果*Ty*是至少有*i*個維度的陣列類型, 則類型查詢會保留*i*所指定之維度中的元素數目。如果*Ty*不是陣列類型, 或其次序小於*I*, 或如果*I*為零, 而*Ty*的類型為「未知界限的`U`陣列」, 則類型查詢會保留值0。

## <a name="example"></a>範例

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[remove_all_extents 類別](../standard-library/remove-all-extents-class.md)\
[remove_extent 類別](../standard-library/remove-extent-class.md)

---
title: extent 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 7463b424d15ee86f851b7d81953abf3fe1c98fee
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519080"
---
# <a name="extent-class"></a>extent 類別

取得陣列維度。

## <a name="syntax"></a>語法

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

*I*<br/>
要查詢的陣列界限

## <a name="remarks"></a>備註

如果*Ty*至少要有陣列類型*我*維度，則類型查詢會保留的項目數中所指定之維度*我*。如果*Ty*不是陣列型別或其等級小於*我*，或如果*我*為零並*Ty*屬於類型"未知界限陣列的`U`」，則類型查詢會保留 0 值。

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

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents 類別](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent 類別](../standard-library/remove-extent-class.md)<br/>

---
title: extent 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e6df4526eea3b0b8b4e91fa4f3e6a89cdd8adb7
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964306"
---
# <a name="extent-class"></a>extent 類別

取得陣列維度。

## <a name="syntax"></a>語法

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>參數

*Ty*要查詢的類型。

*我*陣列繫結至查詢。

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

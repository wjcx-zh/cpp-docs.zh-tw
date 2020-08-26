---
title: '&lt;跨度&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: 7d21023c90472e5c2e1b28d9fa85e517da4a21ae
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846182"
---
# <a name="ltspangt"></a>&lt;跨度&gt;

是一種 `span` 連續的物件序列的觀點。 它提供快速且界限的存取。 `vector`和或不同 `array` 的是，它不會「擁有」它提供存取權的元素。

請參閱 [span 類別](span-class.md) 以取得詳細資訊。 以下是可如何使用範圍的範例：

```cpp
#include <span>
#include <iostream>

void Show(std::span<int> someValues)
{
    // show values in reverse
    for (auto rIt = someValues.rbegin(); rIt != someValues.rend(); ++rIt)
    {
        std::cout << *rIt;
    }

    // show a subspan
    for (auto& i : someValues.subspan(1, 2))
    {
        std::cout << i;
    }
}

int main()
{
    int numbers[]{ 0,1,2,3,4 };
    Show(numbers); // note conversion from array to span
}
```

## <a name="requirements"></a>規格需求

**標頭：**\<span>

**命名空間：** std

**編譯器選項：** /std： c + + 最新

## <a name="members"></a>成員

### <a name="classes"></a>類別

|名稱|描述|
|-|:-|
|[跨度](span-class.md)| 提供一系列連續物件的觀點。 |

### <a name="operators"></a>運算子

|名稱|描述|
|-|:-|
|[運算子 =](span-class.md#op_eq)| 範圍指派 |
|[運算元\[\]](span-class.md#op_at)| 項目存取 |

### <a name="functions"></a>Functions

|名稱|描述|
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| 取得範圍的基礎唯讀位元組。 |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | 取得範圍的基礎位元組。 |

### <a name="constants"></a>常數

|名稱|描述|
|-|:-|
| **dynamic_extent** | 表示在執行時間（而不是編譯時期）決定範圍大小。 當範圍中的專案數在編譯時期為已知時，會指定為 `Extent` 範本參數。 如果在執行時間之前不知道數位，請改為指定 `dynamic_extent` 。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)

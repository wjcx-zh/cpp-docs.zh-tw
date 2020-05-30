---
title: '&lt;跨&gt;'
ms.date: 05/28/2020
f1_keywords:
- <span>
helpviewer_keywords:
- span header
ms.openlocfilehash: ebd0a30c677ea44f95e64e2d2ba010bc99cb412b
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226101"
---
# <a name="ltspangt"></a>&lt;跨&gt;

`span`是連續物件序列的視圖。 它提供快速且界限的存取。 不同 `vector` `array` 于或，它不會「擁有」它提供存取權的元素。 

如需詳細資訊，請參閱[span 類別](span-class.md)。 以下是如何使用 span 的範例：

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

**編譯器選項：** /std： c + + 最新版本

## <a name="members"></a>成員

### <a name="classes"></a>類別

|||
|-|:-|
|[跨](span-class.md)| 提供連續物件序列的視圖。 |

### <a name="operators"></a>操作員

|||
|-|:-|
|[operator =](span-class.md#op_eq)| 範圍指派 |
|[操作\[\]](span-class.md#op_at)| 項目存取 |

### <a name="functions"></a>函式

|||
|-|:-|
| [as_bytes](span-functions.md#as_bytes)| 取得範圍的基礎唯讀位元組。 |
| [as_writable_bytes](span-functions.md#as_writable_bytes) | 取得範圍的基礎位元組。 |

### <a name="constants"></a>常數

|||
|-|:-|
| **dynamic_extent** | 表示在執行時間決定範圍大小，而不是編譯時期。 當範圍中的專案數目在編譯時間為已知時，會將其指定為樣板 `Extent` 參數。 如果在執行時間之前不知道數位，請改為指定 `dynamic_extent` 。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)

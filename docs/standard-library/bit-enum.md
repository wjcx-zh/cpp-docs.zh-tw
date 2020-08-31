---
title: endian 列舉
description: 列舉，用來指定純量類型的位元組型別
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: 78df181e20d0e5d72508bd0fc86118528a312d6b
ms.sourcegitcommit: 3628707bc17c99aac7aac27eb126cc2eaa4d07b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2020
ms.locfileid: "89194536"
---
# <a name="endian-enum"></a>endian 列舉

表示所有純量類型的位元組順序。

## <a name="syntax"></a>Syntax

```cpp
enum class endian {
    little = 0,
    big = 1,
    native = little
 };
```

### <a name="members"></a>成員

|項目|描述|
|-|-|
| `little` | 指出純量類型的位元組由大到小。 也就是說，最不重要的位元組會儲存在最小位址中。 例如， `0x1234` 會儲存 `0x34` `0x12` 。  |
| `big` | 指出純量類型是位元組由大到小，也就是最重要的位元組會儲存在最小位址中。 例如， `0x1234` 會儲存 `0x12` `0x34` 。  |

## <a name="remarks"></a>備註

以 x86、x64、ARM、ARM64) 為 (目標的平臺 Microsoft Visual C++，所有原生純量類型都是位元組由小到大。

## <a name="requirements"></a>規格需求

**標頭：**\<bit>

**命名空間：** std

`/std:c++latest` 是必要項

## <a name="see-also"></a>另請參閱

[\<bit>](../standard-library/bit.md)  

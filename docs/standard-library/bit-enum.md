---
title: 位元組順序列舉
description: 列舉，用來指定純量類型的位元組型別
ms.date: 08/27/2020
f1_keywords:
- bit/std::endian
helpviewer_keywords:
- std::endian
ms.openlocfilehash: b535bc009fbdc0b047444a6bc2ca36eed7a6d1cb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040076"
---
# <a name="endian-enum"></a>位元組順序列舉

表示所有純量類型的位元組順序。

## <a name="syntax"></a>語法

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

## <a name="requirements"></a>需求

**標頭：**\<bit>

**命名空間：** std

[/std：需要最新的 c + +](../build/reference/std-specify-language-standard-version.md) 。

## <a name="see-also"></a>另請參閱

[\<bit>](../standard-library/bit.md)  

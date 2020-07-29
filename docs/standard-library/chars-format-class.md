---
title: chars_format 列舉
ms.date: 07/22/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: 4c1d495c943be02b66d52d1986a783b29a8009c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230178"
---
# <a name="chars_format-enum"></a>chars_format 列舉

與程式庫搭配使用 [\<charconv>](charconv.md) ，以指定基本數值轉換的浮點格式。

## <a name="syntax"></a>語法

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>成員

|元素|描述|
|-|-|
| `scientific` | 導致 `from_chars()` 預期並剖析指數。 它就像是 `'e'` `printf()` 格式規範，其格式為科學標記法，例如`"1.729e+01"` |
| `fixed` | 導致 `from_chars()` 不會預期或剖析指數。 它就像是 `'f'` `printf()` 格式規範，其格式為浮點，例如 `"17.29"` 。|
| `hex` | 會導致 `from_chars()` 預期十六進位格式的數位，但不含前置的 "0x"。 |
| `general` | 導致 `from_chars()` 接受（但不需要）指數。 對於 `to_chars()` ，這就像是在 `g` 科學標記法或固定之間切換的 printf （）格式規範。 它會將指數納入考慮，讓它能夠產生合理的壓縮輸出。 例如：會 `1e-5` 產生 `"1e-05"` ，但會 `1e-4` 產生 `"0.001"` 。 `1e5`會產生 `100000` ，而則會 `1e6` 產生 `1e+06` 。 `1e0`產生 `1` 。|

## <a name="remarks"></a>備註

針對[from_chars](charconv-functions.md#from_chars)函式，此列舉會描述預期的輸入種類。
針對[to_chars](charconv-functions.md#to_chars)函式，它會描述要發出的輸出種類。

## <a name="see-also"></a>另請參閱

[\<charconv>](../standard-library/charconv.md)  
[printf （）格式規範](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

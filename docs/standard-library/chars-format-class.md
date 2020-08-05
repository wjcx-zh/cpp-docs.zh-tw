---
title: chars_format 列舉
ms.date: 08/03/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: d7f95d9bd1522fa0896ccdbac6c1dbc770f2b272
ms.sourcegitcommit: 4eda68a0b3c23d8cefa56b7ba11583412459b32f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565932"
---
# <a name="chars_format-enum"></a>chars_format 列舉

與程式庫搭配使用 [\<charconv>](charconv.md) ，以指定基本數值轉換的浮點格式。

## <a name="syntax"></a>Syntax

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
| `scientific` | 導致 `from_chars()` 預期並剖析指數。 它就像是 `printf()` 格式規範 `'e'` ，其格式為科學標記法，例如 `"1.729e+01"` 。 |
| `fixed` | 導致 `from_chars()` 不會預期或剖析指數。 它就像是 `printf()` 格式規範 `'f'` ，其格式為浮點，例如 `"17.29"` 。|
| `hex` | 會導致 `from_chars()` 預期十六進位格式的數位，但不會有前置字元 `0x` 。 |
| `general` | 使 `from_chars()` 接受 (，但不需要) 指數。 對於 `to_chars()` ，這就像是在 `printf()` `'g'` 科學標記法或固定之間切換的格式規範。 它會將指數納入考慮，讓它能夠產生合理的壓縮輸出。 例如：會 `1e-5` 產生 `"1e-05"` ，但會 `1e-4` 產生 `"0.001"` 。 `1e5`會產生 `100000` ，而則會 `1e6` 產生 `1e+06` 。 `1e0`產生 `1` 。|

## <a name="remarks"></a>備註

針對[from_chars](charconv-functions.md#from_chars)函式，此列舉會描述預期的輸入種類。
針對[to_chars](charconv-functions.md#to_chars)函式，它會描述要發出的輸出種類。

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

/std：需要 c + + 17 或更新版本。

## <a name="see-also"></a>另請參閱

[\<charconv>](../standard-library/charconv.md)  
[printf ( # A1 格式規範](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

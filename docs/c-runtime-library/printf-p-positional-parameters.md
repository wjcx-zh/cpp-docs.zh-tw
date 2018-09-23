---
title: printf_p 位置參數 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef886aad76dd9937e354c071fd707eb6e075f420
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018558"
---
# <a name="printfp-positional-parameters"></a>printf_p 位置參數

位置參數會提供根據數字指定的功能，其中引數會取代至格式字串中的欄位。 您可以使用下列位置參數 `printf` 函式：

| 非位置 printf 函式 | 位置參數的對等項目 |
|---|---|
|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p、_printf_p_l、_wprintf_p、_wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf、_sprintf_l、swprintf、_swprintf_l、\__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p、_sprintf_p_l、_swprintf_p、_swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf、_cprintf_l、_cwprintf、_cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p、_cprintf_p_l、_cwprintf_p、_cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf、_fprintf_l、fwprintf、_fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p、_fprintf_p_l、_fwprintf_p、_fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf、_vprintf_l、vwprintf、_vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf、_vfprintf_l、vfwprintf、_vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p、_vfprintf_p_l、_vfwprintf_p、_vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf、_vsprintf_l、vswprintf、_vswprintf_l、\__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p、_vsprintf_p_l、_vswprintf_p、_vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>如何指定位置參數

### <a name="parameter-indexing"></a>參數索引

如果沒有任何位置格式化，則位置函式的運作方式預設與非位置函式完全相同。 在格式規範的開頭使用 `%n$` 指定位置參數來格式化，其中 `n` 是參數清單中要格式化的參數位置。 格式字串後面的第一個引數，其參數位置從 1 開始。 格式規範的其餘部分會遵循與 `printf` 格式規範相同的規則。 如需有關格式規範的詳細資訊，請參閱[格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。

以下是位置格式化的範例︰

```C
_printf_p("%1$s %2$s", "November", "10");
```

這會列印：

```
November 10
```

所使用的數字順序不需符合引數的順序。 例如，這是有效的格式字串︰

```C
_printf_p("%2$s %1$s", "November", "10");
```

這會列印：

```
10 November
```

不同於傳統的格式字串，位置參數可以在格式字串中使用超過一次。 例如，套用至物件的

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

這會列印：

```
10 times 10 is 100
```

所有引數都必須在格式字串中的某處至少使用一次。 格式字串中允許的位置參數最大數目是由 `_ARGMAX` 所指定。

### <a name="width-and-precision"></a>寬度和精確度

您可以使用 `*n$` 指定位置參數為寬度或精確度規範，其中 `n` 是寬度或精確度參數在參數清單中的位置。 寬度或精確度值的位置必須緊接在 \* 符號之後出現。 例如，套用至物件的

```C
_printf_p("%1$*2$s","Hello", 10);
```

或

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>混合位置和非位置引數

位置參數無法在相同格式字串中與非位置參數混合。 如果使用任何位置格式化，所有的格式規範都必須使用位置格式化。 不過，`printf_p` 和相關的功能仍支援格式字串中的非位置參數不包含任何位置參數。

## <a name="example"></a>範例

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>請參閱

[格式規格語法：printf 和 wprintf 函式](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
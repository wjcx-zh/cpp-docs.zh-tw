---
title: 字元類型
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: 5b1306c70cdab423c8758bf3e6c9ac4e9d6507da
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226486"
---
# <a name="character-types"></a>字元類型

不在字母**L**前面的整數位符常數具有類型 **`int`** 。 整數字元常數的值若包含單一字元，即為解譯為整數的字元數值。 例如，字元 `a` 的數值為 97 (十進位) 和 61 (十六進位)。

在語法上，「寬字元常數」是前面加上字母**L**的字元常數。寬字元常數具有類型，也就 **`wchar_t`** 是在 stddef.h 中定義的整數類型。H 標頭檔。 例如：

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

寬字元常數寬度為 16 位元，並且會指定擴充的執行字元集的成員。 它們可讓您以不太大的字母表達字元，以類型表示 **`char`** 。 如需有關寬字元的詳細資訊，請參閱[多位元組字元和寬字元](../c-language/multibyte-and-wide-characters.md)。

## <a name="see-also"></a>另請參閱

[C 字元常數](../c-language/c-character-constants.md)

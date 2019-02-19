---
title: 字元類型
ms.date: 11/04/2016
helpviewer_keywords:
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
ms.openlocfilehash: f894114d4e980b11edf55c4d4b7c4e60af396fb1
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151581"
---
# <a name="character-types"></a>字元類型

整數字元常數之前若未加上字母 **L**，即屬於 `int` 類型。 整數字元常數的值若包含單一字元，即為解譯為整數的字元數值。 例如，字元 `a` 的數值為 97 (十進位) 和 61 (十六進位)。

在語法上，「寬字元常數」是前面加上字母 **L** 的字元常數。寬字元常數具有類型 `wchar_t`，在 STDDEF.H 標頭檔中定義為整數類型。 例如：

```
char    schar =  'x';   /* A character constant          */
wchar_t wchar = L'x';   /* A wide-character constant for
                            the same character           */
```

寬字元常數寬度為 16 位元，並且會指定擴充的執行字元集的成員。 寬字元常數可用於以字母表示因為太大而無法以 `char` 表示的字元。 如需有關寬字元的詳細資訊，請參閱[多位元組字元和寬字元](../c-language/multibyte-and-wide-characters.md)。

## <a name="see-also"></a>另請參閱

[C 字元常數](../c-language/c-character-constants.md)

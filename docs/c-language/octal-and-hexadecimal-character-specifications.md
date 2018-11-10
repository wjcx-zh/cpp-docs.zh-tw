---
title: 八進位和十六進位字元規格
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: 3fccc6513f3507e4b1763336ac5ecbb78b31d847
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518621"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>八進位和十六進位字元規格

**\\**<em>ooo</em> 的序列表示您可以將 ASCII 字元集中的任何字元指定為三位數的八進位字元碼。 八進位整數的數值會指定所需字元或寬字元的值。

同樣地，**\x**<em>hhh</em> 的序列可讓您將任何 ASCII 字元指定為十六進位字元碼。 例如，您能以一般 C 逸出序列 (**\b**) 指定 ASCII 退格鍵字元，或是將它編碼為 **\010** (八進位) 或 **\x008** (十六進位)。

在八進位逸出序列中只能使用數字 0 到 7。 八進位逸出序列的長度絕不可超過三位數，而且會在遇到不是八進位數字的第一個字元時結束。 雖然您不需要這三個位數全部使用，但是必須至少使用一個。 例如，ASCII 退格鍵字元的八進位表示法為 **\10**，字母 A 則是 **\101**，如 ASCII 圖表中所示。

同樣地，您必須至少針對十六進位逸出序列使用一個位數，不過可以省略第二和第三位數。 因此，您可以將退格鍵字元的十六進位逸出序列指定為 **\x8**、**\x08** 或 **\x008**。

針對字元常數，八進位或十六進位逸出序列的值必須位於 **unsigned char** 類型的可顯示值範圍內。針對寬字元常數，該值則必須位於 `wchar_t` 類型的可顯示值範圍內。 如需寬字元常數的相關資訊，請參閱[多位元組字元和寬字元](../c-language/multibyte-and-wide-characters.md)。

不同於八進位逸出常數，逸出序列中的十六進位數字沒有數目上的限制。 十六進位逸出序列會在遇到不是十六進位數字的第一個字元時結束。 由於十六進位數字包含字母 **a** 到 **f**，因此請務必確定逸出序列會在預期的數字結束。 為了避免混淆，您可以將八進位或十六進位字元定義放在巨集定義中：

```
#define Bell '\x07'
```

對於十六進位值，您可以中斷字串以便清楚顯示正確的值：

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>請參閱

[C 字元常數](../c-language/c-character-constants.md)
---
title: 多位元組字元和寬字元
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- character data types [C]
- Unicode [C++], wide character set
- types [C], character
- characters [C++], wide
- international applications [C++], character display
- multibyte characters [C++]
- wide characters [C++]
- characters [C++], codes
- character codes [C++], wide
- character codes [C++], multibyte
ms.assetid: 1943c469-200d-4724-b18f-781d70520f9e
ms.openlocfilehash: 8e27a1832284c109cc2d8a4655f6d093bf7a2d99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199655"
---
# <a name="multibyte-and-wide-characters"></a>多位元組字元和寬字元

多位元組字元是由一個或多個位元組序列組成的字元。 每個位元組序列表示擴充字元集的單一字元。 多位元組字元用於如漢字等字元集。

寬字元是寬度永遠為 16 位元的多語系字元碼。 字元常數的類型是 **`char`** ; 針對寬字元，類型為 **`wchar_t`** 。 因為寬字元永遠以固定的大小來表示，所以使用寬字元簡化了含國際化字元集的程式設計。

寬字元字串常值 `L"hello"` 會變成類型的六個整數陣列 **`wchar_t`** 。

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Unicode 規格是寬字元的規格。 要在多位元組和寬字元之間轉換的執行階段程式庫常式包括 `mbstowcs`、`mbtowc`、`wcstombs` 和 `wctomb`。

## <a name="see-also"></a>另請參閱

[C 識別碼](../c-language/c-identifiers.md)

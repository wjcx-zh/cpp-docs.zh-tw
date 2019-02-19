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
ms.openlocfilehash: 0d573fac938f5e4d62c99c8cd6e676b96123a0c4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152010"
---
# <a name="multibyte-and-wide-characters"></a>多位元組字元和寬字元

多位元組字元是由一個或多個位元組序列組成的字元。 每個位元組序列表示擴充字元集的單一字元。 多位元組字元用於如漢字等字元集。

寬字元是寬度永遠為 16 位元的多語系字元碼。 字元常數的類型為 `char`，若是寬字元，則其類型為 `wchar_t`。 因為寬字元永遠以固定的大小來表示，所以使用寬字元簡化了含國際化字元集的程式設計。

寬字元字串常值 `L"hello"` 會成為 6 個類型為 `wchar_t` 的整數陣列。

```
{L'h', L'e', L'l', L'l', L'o', 0}
```

Unicode 規格是寬字元的規格。 要在多位元組和寬字元之間轉換的執行階段程式庫常式包括 `mbstowcs`、`mbtowc`、`wcstombs` 和 `wctomb`。

## <a name="see-also"></a>另請參閱

[C 識別項](../c-language/c-identifiers.md)

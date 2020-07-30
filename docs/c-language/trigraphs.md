---
title: 三併詞
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 3ed8849656ac57f4774825294aba7bb41a050eee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227747"
---
# <a name="trigraphs"></a>三併詞

來源字元集 C 原始程式內含在 7 位元的 ASCII 字元集中，但是它是 ISO 646-1983 Invariant Code Set 的超集。 三併詞序列允許 C 程式只使用 ISO (國際標準組織) Invariant Code Set 撰寫。 三併詞是三個字元的序列 (由兩個連續的問號引入)，編譯器會以其對應的標點符號字元取代該序列。 如果 C 原始程式檔所用的字元集不含某些標點符號字元的方便圖形表示，您可改為使用三併詞。

C++17 移除了語言中的三併詞。 實作可能會繼續支援三併詞作為從實體原始程式檔到*基本來源字元集*之實作定義對應的一部分，不過此標準不建議實作這麼做。 直到 C++14，對三併詞的支援與在 C 中一樣。

Visual C++ 會繼續支援三併詞替代，但預設會停用此功能。 如需如何啟用三並詞替代的詳細資訊，請參閱[ `/Zc:trigraphs` （三並詞替代）](../build/reference/zc-trigraphs-trigraphs-substitution.md)。

下表顯示九個三併詞序列。 在標點符號字元的原始程式檔中，所有出現在第一行的字元會以第二行中對應的字元取代。

### <a name="trigraph-sequences"></a>三併詞序列

| 三併詞 | 標點符號字元 |
|----------|-----------------------|
| `??=` | `#` |
| `??(` | `[` |
| `??/` | `\` |
| `??)` | `]` |
| `??'` | `^` |
| `??<` | `{` |
| `??!` | `|` |
| `??>` | `}` |
| `??-` | `~` |

三併詞永遠視為單一來源字元。 三併詞的轉譯會發生在第一個[轉譯階段](../preprocessor/phases-of-translation.md)，接著再辦識字串常值和字元常數中的逸出字元。 其中只會辨認上述表格中顯示的九個三併詞。 其他字元序列會保留為未轉換狀態。

字元逸出序列， **`\?`** 可防止對類似三並詞的字元序列進行解釋。 （如需有關 escape 序列的詳細資訊，請參閱[Escape 序列](../c-language/escape-sequences.md)）。例如，如果您嘗試 `What??!` 使用這個語句列印字串 `printf`

```C
printf( "What??!\n" );
```

印出字串會是 `What|`，因為 `??!` 是使用 `|` 字元取代的三併詞序列。 依如下的陳述式撰寫，以正確列印字串：

```C
printf( "What?\?!\n" );
```

在這個 `printf` 陳述式中，第二個問號前面的反斜線逸出字元會使 `??!` 不會誤譯為三併詞。

## <a name="see-also"></a>另請參閱

[`/Zc:trigraphs`（三並詞替代）](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[C 識別碼](../c-language/c-identifiers.md)

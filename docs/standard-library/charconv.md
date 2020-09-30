---
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: c9dfb8e18a8f7fd367ec4f6b52b1a0af74b3f939
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507711"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

將字元序列快速轉換成整數或浮點值，反之亦然。
使用此程式庫的其中一種方式，是在 JSON 和文字檔中撰寫和往返浮點值。

轉換函式會針對效能進行調整，也支援最短的往返行為。 最短來回行為表示當數位轉換成字元時，只會寫出足夠的精確度，以在將這些字元轉換回浮點數時復原原始數位。 沒有其他 CRT 或 STL 函數可提供這項功能。

使用程式庫的一些優點 `<charconv>` 如下：

- 代表數值的字元序列不需要以 null 終止。 同樣地，當數位轉換成字元時，結果不會以 null 結束。
- 轉換函式不會配置記憶體。 您在所有情況下都擁有緩衝區。
- 轉換函式不會擲回。 它們會傳回包含錯誤資訊的結構。
- 轉換不是執行時間舍入模式敏感性。
- 轉換不感知地區設定。 它們一律會將小數點列印和剖析為 '. '，而不是使用逗號的地區設定。

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

/std：需要 c + + 17 或更新版本。

## <a name="members"></a>成員

### <a name="types"></a>類型

| 類型 | 描述 |
|-|:-|
| [chars_format](chars-format-class.md) | 指定格式類型，例如科學、十六進位等等。 |
| [from_chars_result](from-chars-result-structure.md) | 保留轉換的結果 `from_chars` 。 |
| [to_chars_result](to-chars-result-structure.md) | 保留轉換的結果 `to_chars` 。 |

### <a name="functions"></a>函式

| 函式 | 描述 |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | 將字元轉換成整數、浮點數或雙精度浮點數。 |
| [to_chars](charconv-functions.md#to_chars)| 將整數、浮點數或雙精度浮點數轉換成字元。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)

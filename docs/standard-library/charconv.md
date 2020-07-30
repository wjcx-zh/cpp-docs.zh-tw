---
title: '&lt;charconv&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: 59807749105512e0eb61acfdf60ef463febbc3a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246099"
---
# <a name="ltcharconvgt"></a>&lt;charconv&gt;

將字元序列快速轉換成整數或浮點數，並以另一種方式進行。
使用此程式庫的其中一種方式是在 JSON 和文字檔中寫入浮點值並進行往返。

轉換函式會針對效能進行微調，同時也支援最短的來回行為。 最短的來回行為表示當數位轉換成字元時，只會寫出足夠的精確度，以在將這些字元轉換回浮點時，能夠復原原始數位。 沒有其他 CRT 或 STL 函數提供這項功能。

使用程式庫的優點如下 `<charconv>` ：

- 代表數值的字元序列不需要以 null 結束。 同樣地，當數位轉換成字元時，結果不會以 null 結束。
- 轉換函式不會配置記憶體。 您在所有情況下都擁有該緩衝區。
- 轉換函式不會擲回。 它們會傳回包含錯誤資訊的結構。
- 轉換不會區分執行時間舍入模式。
- 轉換不感知地區設定。 它們一律會針對使用逗號的地區設定，將小數點列印並剖析為 '. ' 永不為 '，'。

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

/std：需要 c + + 17 或更新版本。

## <a name="members"></a>成員

### <a name="types"></a>類型

| 類型 | Description |
|-|:-|
| [chars_format](chars-format-class.md) | 指定格式類型，例如科學、十六進位等等。 |
| [from_chars_result](from-chars-result-structure.md) | 保存轉換的結果 `from_chars` 。 |
| [to_chars_result](to-chars-result-structure.md) | 保存轉換的結果 `to_chars` 。 |

### <a name="functions"></a>函式

| 函式 | 說明 |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | 將字元轉換成整數、浮點數或 double。 |
| [to_chars](charconv-functions.md#to_chars)| 將整數、浮點數或 double 轉換成字元。 |

## <a name="see-also"></a>另請參閱

[標頭檔參考](cpp-standard-library-header-files.md)


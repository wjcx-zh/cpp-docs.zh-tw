---
title: while 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 8095dd8672218239dbcfa879e3df929643e93d90
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231399"
---
# <a name="while-statement-c"></a>while 陳述式 (C)

**`while`** 語句可讓您重複語句，直到指定的運算式變成 false 為止。

## <a name="syntax"></a>語法

*反復專案語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while （**  *運算式*  **）**  *語句*

*expression* 必須有算術或指標類型。 執行程序如下所示：

1. 會對 *expression* 進行評估。

1. 如果*expression*一開始是 false， **`while`** 就永遠不會執行語句的主體，而且控制權會從 **`while`** 語句傳遞至程式中的下一個語句。

   如果 *expression* 為 true (非零)，就會執行陳述式的本體，且從步驟 1 開始重複執行程序。

語句 **`while`** 可能也會在 **`break`** **`goto`** **`return`** 執行語句主體內的、或時終止。 使用 **`continue`** 語句來終止反復專案，而不結束 **`while`** 迴圈。 語句會將 **`continue`** 控制權傳遞至語句的下一個反復專案 **`while`** 。

這是語句的範例 **`while`** ：

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

這個範例會將 `string2` 的字元複製到 `string1`。 如果 `i` 大於或等於 0，會將 `string2[i]` 指派給 `string1[i]` 並遞減 `i`。 當 `i` 達到或低於0時，語句的執行就會 **`while`** 終止。

## <a name="see-also"></a>另請參閱

[while 語句（c + +）](../cpp/while-statement-cpp.md)

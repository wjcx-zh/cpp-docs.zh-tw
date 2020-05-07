---
title: while 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- while
helpviewer_keywords:
- while keyword [C]
- while keyword [C], syntax
ms.assetid: d0c970b8-12a9-4827-afb2-a051111834b7
ms.openlocfilehash: 4a789f248702f33342a19f95710a8ae313da1d94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344729"
---
# <a name="while-statement-c"></a>while 陳述式 (C)

`while` 陳述式可讓您重複陳述式直到指定的運算式變成 false 為止。

## <a name="syntax"></a>語法

*反復專案語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**while （**  *運算式*  **）**  *語句*

*expression* 必須有算術或指標類型。 執行程序如下所示：

1. 會對 *expression* 進行評估。

1. 如果 *expression* 一開始是 false，就永遠不會執行 `while` 陳述式的主體，且控制權會從 `while` 陳述式傳遞至程式的下一個陳述式。

   如果 *expression* 為 true (非零)，就會執行陳述式的本體，且從步驟 1 開始重複執行程序。

在`while`執行語句主體內的**break**、 `goto`或`return`時，語句也可能會終止。 使用 **continue** 陳述式來終止反覆項目，而不需要離開 `while` 迴圈。 **continue** 陳述式會將控制權傳遞至 `while` 陳述式的下一個反覆項目。

這是 `while` 陳述式的範例：

```C
while ( i >= 0 )
{
    string1[i] = string2[i];
    i--;
}
```

這個範例會將 `string2` 的字元複製到 `string1`。 如果 `i` 大於或等於 0，會將 `string2[i]` 指派給 `string1[i]` 並遞減 `i`。 當 `i` 等於或小於 0 時，會終止執行 `while` 陳述式。

## <a name="see-also"></a>請參閱

[while 語句（c + +）](../cpp/while-statement-cpp.md)

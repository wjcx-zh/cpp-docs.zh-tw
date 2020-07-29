---
title: do-while 陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 4a10b9df9f7276eb8e241d76726bca26f2c0cb75
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218867"
---
# <a name="do-while-statement-c"></a>do-while 陳述式 (C)

*do-while* 陳述式可讓您重複陳述式或複合陳述式，直到指定的運算式變成 false 為止。

## <a name="syntax"></a>語法

*反復專案語句*： &nbsp; &nbsp; &nbsp; &nbsp; **`do`** *語句***while （***運算式***）;**        

執行迴圈的主體後，會評估 *do-while* 陳述式中的 *expression*。 因此，迴圈主體一律至少執行一次。

*expression* 必須有算術或指標類型。 執行程序如下所示：

1. 會執行陳述式主體。

1. 接下來會評估 *expression*。 如果 *expression* 為 false，*do-while* 陳述式會終止，而並將控制權傳遞至程式中的下一個陳述式。 如果 *expression* 為 true (非零)，則會從步驟 1 開始重複處理序。

當*do-while* **`break`** 、 **`goto`** 或 **`return`** 語句在語句主體中執行時，do while 語句也可以終止。

這是 *do-while* 陳述式的範例：

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

在這個 *do-while* 陳述式中，會執行 `y = f( x );` 和 `x--;` 兩個陳述式，無論 `x` 的初始值為何。 接下來會評估 `x > 0`。 如果 `x` 大於 0，會再次執行陳述式主體，並重新評估 `x > 0`。 只要 `x` 保持大於 0，陳述式主體就會重複執行。 `x` 變成 0 或負值時，*do-while* 陳述式會終止執行。 迴圈主體至少執行一次。

## <a name="see-also"></a>另請參閱

[do while 語句（c + +）](../cpp/do-while-statement-cpp.md)

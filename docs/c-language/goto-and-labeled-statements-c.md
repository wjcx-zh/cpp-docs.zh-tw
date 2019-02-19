---
title: goto 和標記陳述式 (C)
ms.date: 11/04/2016
f1_keywords:
- goto
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
ms.openlocfilehash: b23e7e6310ba4ed968e2eac8e6d07d81ee4e79ba
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151945"
---
# <a name="goto-and-labeled-statements-c"></a>goto 和標記陳述式 (C)

`goto` 陳述式會將控制項傳輸至標籤。 所指的標籤必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。

## <a name="syntax"></a>語法

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*labeled-statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jump-statement*

*jump-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**goto**  *識別碼*  **;**

*labeled-statement*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*識別碼*  **:**  *陳述式*

陳述式標籤只對 `goto` 陳述式有意義，在任何其他內容中，加上標籤的陳述式都會執行，而不考慮標籤。

*jump-statement* 必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。 `goto` 後面的一組 *identifier* 名稱都有自己的命名空間，因此這些名稱不會干擾其他識別項。 標籤不能重新宣告。 如需詳細資訊，請參閱[命名空間](../c-language/name-spaces.md)。

理想的程式設計風格是盡可能先使用 **break**、**continue** 和 `return` 陳述式，而不是 `goto`。 由於 **break** 陳述式只會從一個迴圈層級結束，因此可能需要使用 `goto` 才能從深層的巢狀迴圈內結束迴圈。

這個範例將示範 `goto` 陳述式：

```
// goto.c
#include <stdio.h>

int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 3; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 5 )
                goto stop;
        }
    }

    /* This message does not print: */
    printf_s( "Loop exited. i = %d\n", i );

    stop: printf_s( "Jumped to stop. i = %d\n", i );
}
```

在這個範例中，當 `goto` 等於 5 時，`stop` 陳述式會將控制項傳送至標記 `i` 的點。

## <a name="see-also"></a>另請參閱

[陳述式](../c-language/statements-c.md)

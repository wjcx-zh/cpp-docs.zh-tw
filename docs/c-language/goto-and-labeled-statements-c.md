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
ms.openlocfilehash: d84aa6701ef030dc494f6a40a7223d6f9bcd5073
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87199980"
---
# <a name="goto-and-labeled-statements-c"></a>goto 和標記陳述式 (C)

語句會將 **`goto`** 控制項傳輸至標籤。 所指的標籤必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。

## <a name="syntax"></a>語法

*語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*加上標籤的語句*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*跳躍語句*

*跳躍語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`goto`**  *識別碼*  **;**

加上*標籤的語句*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*  **：**  *語句*

語句標籤只對語句有意義 **`goto`** ; 在任何其他內容中，會執行標示的語句，而不考慮標籤。

*jump-statement* 必須位於相同的函式中，而且只能出現在相同函式中的單獨一個陳述式前面。 後面的一組*識別碼*名稱 **`goto`** 有自己的命名空間，因此這些名稱不會干擾其他識別碼。 標籤不能重新宣告。 如需詳細資訊，請參閱[命名空間](../c-language/name-spaces.md)。

這是很好的程式設計風格 **`break`** ，可盡可能使用、 **`continue`** 和 **`return`** 語句 **`goto`** 。 由於 **`break`** 語句只會從一個迴圈層級結束，因此 **`goto`** 可能需要從深度的嵌套迴圈中結束迴圈。

這個範例會示範 **`goto`** 語句：

```c
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

在此範例中， **`goto`** `stop` 當等於5時，語句會將控制項傳輸至標示的點 `i` 。

## <a name="see-also"></a>另請參閱

[陳述式](../c-language/statements-c.md)

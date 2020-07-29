---
title: goto 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: e56ebfadea0d643ac68e2ace722a39587bd01312
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223703"
---
# <a name="goto-statement-c"></a>goto 陳述式 (C++)

**`goto`** 語句會無條件地將控制權轉移至指定之識別碼所標記的語句。

## <a name="syntax"></a>語法

```
goto identifier;
```

## <a name="remarks"></a>備註

`identifier` 所指定之標記的陳述式必須位於目前的函式。 所有 `identifier` 名稱是內部命名空間的成員，因此不會干擾其他識別項。

語句標籤只對語句有意義 **`goto`** ，否則會忽略語句標籤。 標籤不能重新宣告。

**`goto`** 不允許使用語句將控制權轉移至位置，而該位置會略過該位置範圍內任何變數的初始化。 下列範例會引發 C2362：

```cpp
int goto_fn(bool b)
{
    if (!b)
    {
        goto exit;  // C2362
    }
    else
    { /*...*/ }

    int error_code = 42;

exit:
    return error_code;
}
```

這是很好的程式設計風格 **`break`** ，盡可能使用、 **`continue`** 和 **`return`** 語句，而不是 **`goto`** 語句。 不過，因為 **`break`** 語句只會從一個迴圈層級結束，所以您可能必須使用 **`goto`** 語句來結束深度的嵌套迴圈。

如需標籤和語句的詳細資訊 **`goto`** ，請參閱[標記的語句](../cpp/labeled-statements.md)。

## <a name="example"></a>範例

在此範例中， **`goto`** 語句會將控制項傳輸至 `stop` `i` 等於3的點。

```cpp
// goto_statement.cpp
#include <stdio.h>
int main()
{
    int i, j;

    for ( i = 0; i < 10; i++ )
    {
        printf_s( "Outer loop executing. i = %d\n", i );
        for ( j = 0; j < 2; j++ )
        {
            printf_s( " Inner loop executing. j = %d\n", j );
            if ( i == 3 )
                goto stop;
        }
    }

    // This message does not print:
    printf_s( "Loop exited. i = %d\n", i );

    stop:
    printf_s( "Jumped to stop. i = %d\n", i );
}
```

```Output
Outer loop executing. i = 0
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 1
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 2
Inner loop executing. j = 0
Inner loop executing. j = 1
Outer loop executing. i = 3
Inner loop executing. j = 0
Jumped to stop. i = 3
```

## <a name="see-also"></a>另請參閱

[跳躍陳述式](../cpp/jump-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)

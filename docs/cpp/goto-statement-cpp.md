---
title: goto 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- goto_cpp
helpviewer_keywords:
- goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
ms.openlocfilehash: aac308905a01a52a4ce5ee0fa3be03f2f33ac1cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153693"
---
# <a name="goto-statement-c"></a>goto 陳述式 (C++)

**Goto**陳述式無條件地將控制權傳輸至指定的識別項所標記的陳述式。

## <a name="syntax"></a>語法

```
goto identifier;
```

## <a name="remarks"></a>備註

`identifier` 所指定之標記的陳述式必須位於目前的函式。 所有 `identifier` 名稱是內部命名空間的成員，因此不會干擾其他識別項。

陳述式標籤是僅有意義**goto**陳述式; 否則會忽略陳述式標籤。 標籤不能重新宣告。

A **goto**陳述式不允許將控制權移轉給略過該位置中的範圍內的任何變數的初始化的位置。 下列範例會引發 C2362:

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

它是理想的程式設計風格，使用**中斷**，**繼續**，和**傳回**陳述式，而不是**goto**陳述式時可能的。 不過，因為**中斷**陳述式會結束迴圈的只有一個層級，您可能必須使用**goto**陳述式來結束深度巢狀的迴圈。

如需標籤和**goto**陳述式，請參閱[標記陳述式](../cpp/labeled-statements.md)。

## <a name="example"></a>範例

在此範例中， **goto**陳述式將控制權傳輸至標示的點`stop`當`i`等於 3。

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

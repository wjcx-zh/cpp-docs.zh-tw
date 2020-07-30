---
title: while 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 168b1fc20d165c44c3230a8d1094c99b689ddbb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233544"
---
# <a name="while-statement-c"></a>while 陳述式 (C++)

重複執行*語句*，直到*expression*評估為零為止。

## <a name="syntax"></a>語法

```
while ( expression )
   statement
```

## <a name="remarks"></a>備註

*運算式*的測試會在每次執行迴圈之前進行;因此， **`while`** 迴圈會執行零次或多次。 *運算式*必須是整數類資料類型、指標類型，或是明確轉換成整數或指標類型的類別類型。

在 **`while`** 語句主體中執行[break](../cpp/break-statement-cpp.md)、 [goto](../cpp/goto-statement-cpp.md)或[return](../cpp/return-statement-cpp.md)時，迴圈也可以終止。 請使用 [[繼續](../cpp/continue-statement-cpp.md)] 終止目前的反復專案，而不結束 **`while`** 迴圈。 **`continue`** 將控制權傳遞給迴圈的下一個反復專案 **`while`** 。

下列程式碼會使用 **`while`** 迴圈來修剪字串尾端的底線：

```cpp
// while_statement.cpp

#include <string.h>
#include <stdio.h>
char *trim( char *szSource )
{
    char *pszEOS = 0;

    //  Set pointer to character before terminating NULL
    pszEOS = szSource + strlen( szSource ) - 1;

    //  iterate backwards until non '_' is found
    while( (pszEOS >= szSource) && (*pszEOS == '_') )
        *pszEOS-- = '\0';

    return szSource;
}
int main()
{
    char szbuf[] = "12345_____";

    printf_s("\nBefore trim: %s", szbuf);
    printf_s("\nAfter trim: %s\n", trim(szbuf));
}
```

終止條件在迴圈頂端進行評估。 如果沒有結尾底線，此迴圈絕不會執行。

## <a name="see-also"></a>另請參閱

[反覆運算陳述式](../cpp/iteration-statements-cpp.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)<br/>
[do while 語句（c + +）](../cpp/do-while-statement-cpp.md)<br/>
[for 語句（c + +）](../cpp/for-statement-cpp.md)<br/>
[以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)

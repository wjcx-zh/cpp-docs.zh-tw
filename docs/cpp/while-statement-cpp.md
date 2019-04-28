---
title: while 陳述式 (C++)
ms.date: 11/04/2016
f1_keywords:
- while_cpp
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
ms.openlocfilehash: 669618e9807109be18117968b1f5b6f49ec15e07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325412"
---
# <a name="while-statement-c"></a>while 陳述式 (C++)

執行*陳述式*之前重複*運算式*評估為零。

## <a name="syntax"></a>語法

```
while ( expression )
   statement
```

## <a name="remarks"></a>備註

測試*運算式*迴圈; 每次執行之前將因此**雖然**迴圈會執行零次以上。 *運算式*必須是整數類資料類型、 指標類型，或類別類型，可明確轉換為整數或指標類型。

A**雖然**迴圈也可能終止時[中斷](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[傳回](../cpp/return-statement-cpp.md)陳述式內執行主體。 使用[繼續](../cpp/continue-statement-cpp.md)終止目前的反覆項目，而不結束**雖然**迴圈。 **繼續**會將控制項傳遞到下一個反覆運算**雖然**迴圈。

下列程式碼會使用**雖然**迴圈修剪尾端底線從字串：

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
[do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)<br/>
[for 陳述式 (C++)](../cpp/for-statement-cpp.md)<br/>
[以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)
---
title: 編譯器錯誤 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 03b54fe2373063c8c0f9905da93822928392998d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209019"
---
# <a name="compiler-error-c2001"></a>編譯器錯誤 C2001

常數中的新行

字串常數，無法繼續第二行，除非您執行下列作業：

- 結尾加上反斜線的第一行。

- 關閉第一列中利用雙引號字串並在下一行的字串以開啟另一個雙引號。

結束 \n 的第一行是不夠的。

## <a name="example"></a>範例

下列範例會產生 C2001:

```
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

## <a name="example"></a>範例

行接續字元之後的下一行的開頭的空格會包含在字串常數。 沒有任何範例如上所示在字串常數內嵌新行字元。 您可以將內嵌新行字元，如下所示：

```
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
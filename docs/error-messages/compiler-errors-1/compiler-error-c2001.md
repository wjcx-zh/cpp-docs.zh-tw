---
title: 編譯器錯誤 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 2bf9bd322812764b2f63493d4b22b58d853a25fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756834"
---
# <a name="compiler-error-c2001"></a>編譯器錯誤 C2001

常數中的分行符號

除非您執行下列動作，否則字串常數不能繼續在第二行：

- 以反斜線結尾的第一行。

- 使用雙引號關閉第一行中的字串，然後在下一行以另一個雙引號開啟字串。

以 \n 結尾的第一行並不足夠。

## <a name="example"></a>範例

下列範例會產生 C2001：

```cpp
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

在字串常數中包含行接續字元之後，下一行開頭的空格。 以上所示的範例都不會將分行符號內嵌至字串常數。 您可以內嵌分行符號，如下所示：

```cpp
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

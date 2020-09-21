---
title: 編譯器錯誤 C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 6b40a3bd186b5c45a0ea5163f433635ab1e7b07f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743486"
---
# <a name="compiler-error-c2001"></a>編譯器錯誤 C2001

常數中的分行符號

除非您執行下列動作，否則字串常數無法在第二行繼續：

- 以反斜線結尾第一行。

- 以雙引號關閉第一行的字串，並以另一個雙引號開啟下一行中的字串。

以 \n 結束第一行的程式碼並不足夠。

## <a name="examples"></a>範例

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

行接續字元之後，下一行開頭的空格會包含在字串常數中。 以上所示的範例都不會將分行符號內嵌到字串常數中。 您可以內嵌分行符號，如下所示：

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

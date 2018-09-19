---
title: 編譯器錯誤 C2001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 71048a706678e4d9e6906972ebf148748927e829
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088238"
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
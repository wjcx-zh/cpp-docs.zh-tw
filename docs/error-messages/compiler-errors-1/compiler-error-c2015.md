---
title: 編譯器錯誤 C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 5453009e1c2bd091ed3507f3c43bd7fcecd33abc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743096"
---
# <a name="compiler-error-c2015"></a>編譯器錯誤 C2015

常數中有太多字元

字元常數包含兩個以上的字元。 限制是標準字元常數的一個字元，而兩個字元用於長字元常數。

Escape 序列（例如 \t）會轉換成單一字元。

## <a name="examples"></a>範例

下列範例會產生 C2015：

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

使用 Microsoft 擴充功能時，也會發生 C2015 轉換成整數的字元常數。  下列範例會產生 C2015：

```cpp
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```

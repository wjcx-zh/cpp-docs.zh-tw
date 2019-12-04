---
title: 編譯器錯誤 C2015
ms.date: 11/04/2016
f1_keywords:
- C2015
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
ms.openlocfilehash: 83b78336d74037b9f9f52da8327479f506db1ffc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751063"
---
# <a name="compiler-error-c2015"></a>編譯器錯誤 C2015

常數中有太多字元

字元常數包含兩個以上的字元。 限制是標準字元常數的一個字元，長字元常數則是兩個字元。

Escape 序列（例如 \t）會轉換成單一字元。

## <a name="example"></a>範例

下列範例會產生 C2015：

```cpp
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>範例

使用 Microsoft 擴充功能時，也可能會發生 C2015，並將字元常數轉換成整數。  下列範例會產生 C2015：

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

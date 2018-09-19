---
title: 編譯器錯誤 C2015 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2015
dev_langs:
- C++
helpviewer_keywords:
- C2015
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb9c3ba86224906f749088b96e5daae364d99e2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076043"
---
# <a name="compiler-error-c2015"></a>編譯器錯誤 C2015

常數中有太多字元

字元常數中包含兩個以上的字元。 標準字元常數的一個字元和兩個字元長的字元常數的限制。

逸出序列，例如 \t，會轉換成單一字元。

## <a name="example"></a>範例

下列範例會產生 C2015:

```
// C2015.cpp
// compile with: /c

char test1 = 'error';   // C2015
char test2 = 'e';   // OK
```

## <a name="example"></a>範例

使用 Microsoft 擴充功能，轉換為整數字元常數時，也會發生 C2015。  下列範例會產生 C2015:

```
// C2015b.cpp
#include <stdio.h>

int main()
{
    int a = 'abcde';   // C2015

    int b = 'a';   // 'a' = ascii 0x61
    printf_s("%x\n", b);
}
```
---
title: 編譯器錯誤 C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 37d32285f9c01efb981c5f02acba21f2d6fe3dc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165657"
---
# <a name="compiler-error-c2041"></a>編譯器錯誤 C2041

不合法的數字的基底 'number'，' character'

指定的字元不是有效的數字 （例如八進位或十六進位） 基底。

下列範例會產生 C2041:

```
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

可能的解決方式：

```
// C2041b.cpp
// compile with: /c
int j = 071;
```
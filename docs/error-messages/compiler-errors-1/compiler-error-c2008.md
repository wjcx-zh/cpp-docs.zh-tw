---
title: 編譯器錯誤 C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 292f5c6ab9a4e14077f848ff57ff08adefeb09a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757328"
---
# <a name="compiler-error-c2008"></a>編譯器錯誤 C2008

'character'：未預期會出現在巨集定義中

字元會緊接在宏名稱之後出現。 若要解決此錯誤，宏名稱後面必須有一個空格。

下列範例會產生 C2008：

```cpp
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

可能的解決方案：

```cpp
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```

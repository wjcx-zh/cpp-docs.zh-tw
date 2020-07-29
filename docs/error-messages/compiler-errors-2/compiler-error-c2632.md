---
title: 編譯器錯誤 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: 8ea3a106e8819bf067203f220ca51e17b87bfe46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225458"
---
# <a name="compiler-error-c2632"></a>編譯器錯誤 C2632

' type1 ' 後面接著 ' type2 ' 是不合法的

如果兩個類型規範之間的程式碼遺失，可能會導致此錯誤。

下列範例會產生 C2632：

```cpp
// C2632.cpp
int float i;   // C2632
```

針對 Visual Studio .NET 2003 所做的編譯器一致性工作，也可能會產生此錯誤。 **`bool`** 現在是正確的類型。 在舊版中， **`bool`** 是 typedef，而您可以使用該名稱建立識別碼。

下列範例會產生 C2632：

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解決此錯誤，使程式碼在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++ 中都有效，請重新命名識別碼。

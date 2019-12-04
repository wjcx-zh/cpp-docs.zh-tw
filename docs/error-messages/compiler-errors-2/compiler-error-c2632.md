---
title: 編譯器錯誤 C2632
ms.date: 11/04/2016
f1_keywords:
- C2632
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
ms.openlocfilehash: f69d43bf50f5f13957e49d1e9ffa798a3db5a7b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754689"
---
# <a name="compiler-error-c2632"></a>編譯器錯誤 C2632

' type1 ' 後面接著 ' type2 ' 是不合法的

如果兩個類型規範之間的程式碼遺失，可能會導致此錯誤。

下列範例會產生 C2632：

```cpp
// C2632.cpp
int float i;   // C2632
```

針對 Visual Studio .NET 2003 所做的編譯器一致性工作，也可能會產生此錯誤。 `bool` 現在是正確的類型。 在舊版中，`bool` 是 typedef，而您可以使用該名稱建立識別碼。

下列範例會產生 C2632：

```cpp
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解決此錯誤，讓程式碼在 Visual Studio .NET 2003 和 Visual Studio .NET 版本的 Visual C++中都有效，請重新命名識別碼。

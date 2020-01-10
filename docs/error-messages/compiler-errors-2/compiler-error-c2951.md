---
title: 編譯器錯誤 C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755976"
---
# <a name="compiler-error-c2951"></a>編譯器錯誤 C2951

類型宣告只允許用於全域、命名空間或類別範圍

您不能在全域或命名空間範圍外宣告泛型或範本類別。 如果您在 include 檔案中進行一般或範本宣告，請確定 include 檔案位於全域範圍內。

下列範例會產生 C2951：

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

使用泛型時，也會發生 C2951：

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```

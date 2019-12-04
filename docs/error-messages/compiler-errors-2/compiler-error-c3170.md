---
title: 編譯器錯誤 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761760"
---
# <a name="compiler-error-c3170"></a>編譯器錯誤 C3170

專案中不能有不同的模組識別碼

在編譯中的兩個檔案中，發現具有不同名稱的[模組](../../windows/module-cpp.md)屬性。 每一次編譯只能指定一個唯一的 `module` 屬性。

可以在一個以上的原始程式碼檔案中指定相同的 `module` 屬性。

例如，如果找到下列模組屬性：

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

然後，

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

編譯器會產生 C3170 （請注意不同的名稱）。

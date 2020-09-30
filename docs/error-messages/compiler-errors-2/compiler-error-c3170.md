---
title: 編譯器錯誤 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: c4eb4a2551312791d05c8badb66af0070e74b630
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508332"
---
# <a name="compiler-error-c3170"></a>編譯器錯誤 C3170

專案中不能有不同的模組識別碼

在編譯中的兩個檔案中找到具有不同名稱的[模組](../../windows/attributes/module-cpp.md)屬性。 `module`每個編譯只能指定一個唯一的屬性。

您 `module` 可以在一個以上的原始程式碼檔案中指定相同的屬性。

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

編譯器會產生 C3170 (請注意) 的不同名稱。

---
title: 編譯器錯誤 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761747"
---
# <a name="compiler-error-c3171"></a>編譯器錯誤 C3171

' module '：不能在專案中指定不同的模組屬性

在編譯中的兩個檔案中找到具有不同參數清單的[模組](../../windows/module-cpp.md)屬性。 每一次編譯只能指定一個唯一的 `module` 屬性。

可以在一個以上的原始程式碼檔案中指定相同的 `module` 屬性。

例如，如果找到下列 `module` 屬性：

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

然後，

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

編譯器會產生 C3171 （請注意不同的版本值）。

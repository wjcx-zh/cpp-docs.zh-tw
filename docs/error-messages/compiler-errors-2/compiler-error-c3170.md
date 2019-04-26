---
title: 編譯器錯誤 C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174701"
---
# <a name="compiler-error-c3170"></a>編譯器錯誤 C3170

不能在專案中有不同的模組識別碼

[模組](../../windows/module-cpp.md)兩個在編譯檔案中找不到具有不同名稱的屬性。 只有一個唯一`module`屬性可以指定每次編譯。

相同`module`屬性可以指定多個原始程式碼檔中。

比方說，如果找不到下列的模組屬性：

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

然後，

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

編譯器會產生 C3170 （請注意不同的名稱）。
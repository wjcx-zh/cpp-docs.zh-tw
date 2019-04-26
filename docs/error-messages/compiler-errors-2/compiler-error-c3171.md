---
title: 編譯器錯誤 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175423"
---
# <a name="compiler-error-c3171"></a>編譯器錯誤 C3171

'module': 無法在專案中指定不同的模組屬性

[模組](../../windows/module-cpp.md)在兩個在編譯檔案中找不到具有不同參數清單的屬性。 只有一個唯一`module`屬性可以指定每次編譯。

相同`module`屬性可以指定多個原始程式碼檔中。

例如，如果下列`module`找不到屬性：

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

然後，

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

編譯器會產生 C3171 （請注意不同的版本值）。
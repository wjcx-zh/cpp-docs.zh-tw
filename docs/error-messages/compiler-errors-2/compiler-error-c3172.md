---
title: 編譯器錯誤 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 5c9c1561b63c740b9f7f5d85b2bf3e04de2542c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514942"
---
# <a name="compiler-error-c3172"></a>編譯器錯誤 C3172

'模組名稱': 無法在專案中指定不同的 idl_module 屬性

[idl_module](../../windows/idl-module.md)屬性具有相同名稱但不同`dllname`或`version`兩個在編譯檔案中找不到參數。 只有一個唯一`idl_module`屬性可以指定每次編譯。

相同`idl_module`屬性可以指定多個原始程式碼檔中。

例如，如果下列`idl_module`找不到屬性：

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

然後，

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

編譯器會產生 C3172 （請注意不同的版本值）。
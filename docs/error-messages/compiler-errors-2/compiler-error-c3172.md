---
title: 編譯器錯誤 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761734"
---
# <a name="compiler-error-c3172"></a>編譯器錯誤 C3172

' module_name '：不能在專案中指定不同的 idl_module 屬性

在編譯中的兩個檔案中找到相同名稱但不同 `dllname` 或 `version` 參數的[idl_module](../../windows/idl-module.md)屬性。 每一次編譯只能指定一個唯一的 `idl_module` 屬性。

可以在一個以上的原始程式碼檔案中指定相同的 `idl_module` 屬性。

例如，如果找到下列 `idl_module` 屬性：

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

然後，

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

編譯器會產生 C3172 （請注意不同的版本值）。

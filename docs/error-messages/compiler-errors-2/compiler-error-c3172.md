---
title: 編譯器錯誤 C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: ca0eab35f6e60d81a324156905619ceb7ace8830
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508292"
---
# <a name="compiler-error-c3172"></a>編譯器錯誤 C3172

' module_name '：無法在專案中指定不同的 idl_module 屬性

[idl_module](../../windows/attributes/idl-module.md)在編譯中的 `dllname` `version` 兩個檔案中找到具有相同名稱但不同或參數的 idl_module 屬性。 `idl_module`每個編譯只能指定一個唯一的屬性。

您 `idl_module` 可以在一個以上的原始程式碼檔案中指定相同的屬性。

例如，如果 `idl_module` 找到下列屬性：

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

編譯器會產生 C3172 (請注意) 的不同版本值。

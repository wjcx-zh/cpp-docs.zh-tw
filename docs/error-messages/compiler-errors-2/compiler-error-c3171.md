---
title: 編譯器錯誤 C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 14f0cedc5448005a29d74f05ae3e68e74eb5cf1c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508298"
---
# <a name="compiler-error-c3171"></a>編譯器錯誤 C3171

' module '：無法在專案中指定不同的模組屬性

在編譯中的兩個檔案中找到具有不同參數清單的[模組](../../windows/attributes/module-cpp.md)屬性。 `module`每個編譯只能指定一個唯一的屬性。

您 `module` 可以在一個以上的原始程式碼檔案中指定相同的屬性。

例如，如果 `module` 找到下列屬性：

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

編譯器會產生 C3171 (請注意) 的不同版本值。

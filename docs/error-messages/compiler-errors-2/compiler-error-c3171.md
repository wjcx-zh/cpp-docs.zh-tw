---
title: 編譯器錯誤 C3171 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082257"
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
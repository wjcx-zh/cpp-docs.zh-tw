---
title: 編譯器錯誤 C2178 |Microsoft Docs
ms.custom: ''
ms.date: 05/08/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af9efdb3258e6793a17a26b552df8ba4e63c9107
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102331"
---
# <a name="compiler-error-c2178"></a>編譯器錯誤 C2178

'*識別碼*'不可以宣告使用'*規範*' 規範

A`mutable`規範使用在宣告中，但在此內容中不允許規範。

`mutable`規範可以只會套用至類別資料成員的名稱，但不可套用至宣告的名稱`const`或`static`，但不可套用至參考的成員。

## <a name="example"></a>範例

下列範例會示範如何 C2178 可能會發生，以及如何修正此問題。

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```

---
title: 編譯器錯誤 C2632 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2632
dev_langs:
- C++
helpviewer_keywords:
- C2632
ms.assetid: b15a6b1b-42d2-4e1b-8660-e6bfde61052d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bf03c35c60bebb52c94ed04cca2349f35c06fbc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093646"
---
# <a name="compiler-error-c2632"></a>編譯器錯誤 C2632

'type1' 後面接著 'type2' 是不合法

如果遺漏之間兩個型別規範中的程式碼，就可能造成此錯誤。

下列範例會產生 C2632:

```
// C2632.cpp
int float i;   // C2632
```

也可因為針對 Visual Studio.NET 2003年所進行的編譯器一致性處理而產生這個錯誤。 `bool` 現在是適當的型別。 在舊版中，`bool`的 typedef，以及您可以建立具有該名稱的識別碼。

下列範例會產生 C2632:

```
// C2632_2.cpp
// compile with: /LD
void f(int bool);   // C2632
```

若要解決這個錯誤，以便的程式碼是有效的 Visual c + + 的 Visual Studio.NET 2003年和 Visual Studio.NET 版本中，重新命名識別項。
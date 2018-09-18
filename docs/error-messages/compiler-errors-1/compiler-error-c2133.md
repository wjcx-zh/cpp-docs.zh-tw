---
title: 編譯器錯誤 C2133 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2133
dev_langs:
- C++
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169b24787f1b180c7ba70c5d779e341e60ea2150
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025187"
---
# <a name="compiler-error-c2133"></a>編譯器錯誤 C2133

'identifier': 未知的大小

可變大小的陣列宣告為類別、 結構、 等位或列舉的成員。 /Za (ANSI C) 選項不允許成員可變大小的陣列。

下列範例會產生 C2133:

```
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

可能的解決方式：

```
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```
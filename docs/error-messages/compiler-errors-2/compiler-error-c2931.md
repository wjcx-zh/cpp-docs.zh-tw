---
title: 編譯器錯誤 C2931 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2931
dev_langs:
- C++
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68c7f3a2525974c1d6c2cc26719e284538cae332
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023549"
---
# <a name="compiler-error-c2931"></a>編譯器錯誤 C2931

'class': type-class-id 重複定義為 'identifier' 的成員函式

您無法使用泛型或樣板類別作為另一個類別的成員函式。

此錯誤可能是大括弧不對稱所造成。

下列範例會產生 C2931：

```
// C2931.cpp
// compile with: /c
template<class T>
struct TC { };
struct MyStruct {
   void TC<int>();   // C2931
};

struct TC2 { };
struct MyStruct2 {
   void TC2();
};
```

使用泛型時，也會發生 C2931：

```
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```
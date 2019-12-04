---
title: 編譯器錯誤 C2931
ms.date: 11/04/2016
f1_keywords:
- C2931
helpviewer_keywords:
- C2931
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
ms.openlocfilehash: 03c5c1865343afdc0fd7a67ce393c7e1a5d2966f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757692"
---
# <a name="compiler-error-c2931"></a>編譯器錯誤 C2931

'class': type-class-id 重複定義為 'identifier' 的成員函式

您無法使用泛型或樣板類別作為另一個類別的成員函式。

此錯誤可能是大括弧不對稱所造成。

下列範例會產生 C2931：

```cpp
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

```cpp
// C2931b.cpp
// compile with: /clr /c
generic<class T> ref struct GC {};
struct MyStruct {
   void GC<int>();   // C2931
   void GC2();   // OK
};
```

---
title: 編譯器錯誤 C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 82042b851282e686719ed54ccad0a2802afda22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761015"
---
# <a name="compiler-error-c2921"></a>編譯器錯誤 C2921

redefinition : 'class' : class 範本或泛型將會宣告為 'type'

泛型或範本類別有多個不相等的宣告。 若要修正此錯誤，請對不同的類型使用不同的名稱，或移除類型名稱的重複定義。

下列範例會產生 C2921：

```cpp
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

使用泛型時，也會發生 C2921。

```cpp
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```

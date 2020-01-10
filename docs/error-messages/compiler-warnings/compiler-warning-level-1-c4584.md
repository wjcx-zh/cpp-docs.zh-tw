---
title: 編譯器警告（層級1） C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966240"
---
# <a name="compiler-warning-level-1-c4584"></a>編譯器警告（層級1） C4584

' class1 '：基類 ' class2 ' 已經是 ' a.class3 ' 的基類

您定義的類別繼承自兩個類別，其中一個會繼承自另一個。 例如:

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

在此情況下，類別 C 會發出警告，因為它繼承自類別 A 和類別 B，這也會繼承自類別 A。此警告會提醒您，您必須完整限定使用這些基類中的成員，否則將會產生編譯器錯誤，因為您所參考的類別成員不明確。
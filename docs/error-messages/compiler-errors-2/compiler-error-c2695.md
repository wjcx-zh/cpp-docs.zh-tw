---
title: 編譯器錯誤 C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 6d46699a2036c4f45daf3c34802ddb6b44e554ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755209"
---
# <a name="compiler-error-c2695"></a>編譯器錯誤 C2695

' function1 '：覆寫虛擬函式與 ' function2 ' 的差異只在於呼叫慣例

衍生類別中函式的簽章無法覆寫基類中的函式，以及變更呼叫慣例。

下列範例會產生 C2695：

```cpp
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```

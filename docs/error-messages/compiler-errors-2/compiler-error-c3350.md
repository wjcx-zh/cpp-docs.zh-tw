---
title: 編譯器錯誤 C3350
ms.date: 11/04/2016
f1_keywords:
- C3350
helpviewer_keywords:
- C3350
ms.assetid: cfbbc338-92b5-4f34-999e-aa2d2376bc70
ms.openlocfilehash: 39d4b4c1cef0febe8845db3e74799b2d240dbdb3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736954"
---
# <a name="compiler-error-c3350"></a>編譯器錯誤 C3350

'delegate': 委派建構函式必須有 <數字> 個引數

當您建立委派的執行個體時，必須傳遞兩個引數：包含委派函式之類型的執行個體，以及函式。

下列範例會產生 C3350：

```cpp
// C3350.cpp
// compile with: /clr
delegate void SumDelegate();

public ref class X {
public:
   void F() {}
   static void F2() {}
};

int main() {
   X ^ MyX = gcnew X();
   SumDelegate ^ pSD = gcnew SumDelegate();   // C3350
   SumDelegate ^ pSD1 = gcnew SumDelegate(MyX, &X::F);
   SumDelegate ^ pSD2 = gcnew SumDelegate(&X::F2);
}
```

---
title: 編譯器錯誤 C2553
ms.date: 11/04/2016
f1_keywords:
- C2553
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
ms.openlocfilehash: aa3e97d576e994878ab5b080363c4c09b79f42ed
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756782"
---
# <a name="compiler-error-c2553"></a>編譯器錯誤 C2553

' base_function '：覆寫虛擬函式傳回類型與 ' override_function ' 不同

衍生類別中的函式嘗試覆寫基類中的虛擬函式，但衍生的類別函式沒有與基類函數相同的傳回類型。  覆寫函式簽章必須符合所要覆寫之函數的簽章。

下列範例會產生 C2553：

```cpp
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```

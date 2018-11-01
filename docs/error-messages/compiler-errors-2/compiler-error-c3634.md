---
title: 編譯器錯誤 C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 2acd76fee5e7ca309991e639044a45ea83ed112b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50527539"
---
# <a name="compiler-error-c3634"></a>編譯器錯誤 C3634

'function': 無法定義 managed 或 WinRTclass 抽象方法

抽象方法可以在 Managed 或 WinRT 類別中宣告，但無法定義。

## <a name="example"></a>範例

下列範例會產生 C3634：

```
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```

---
title: 編譯器錯誤 C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 73fd3188fd1ee4c95d8444bea0f3c05beefa478f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760221"
---
# <a name="compiler-error-c2691"></a>編譯器錯誤 C2691

' 資料類型 '： managed 或 WinRTarray 不能有此元素類型

受管理或 WinRT 陣列項目的類型可以是值類型或參考類型。

下列範例會產生 C2691：

```cpp
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```

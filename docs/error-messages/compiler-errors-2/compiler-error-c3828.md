---
title: 編譯器錯誤 C3828
ms.date: 11/04/2016
f1_keywords:
- C3828
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
ms.openlocfilehash: f499bb2a8fd6d3148935daec89835b79d2ff5b49
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770547"
---
# <a name="compiler-error-c3828"></a>編譯器錯誤 C3828

'object type': 正在建立的執行個體受管理時，不允許的位置引數或 WinRTclasses

建立 managed 的類型或 Windows 執行階段類型的物件時，您無法使用運算子的位置形式[ref new 和 gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)或是[新](../../cpp/new-operator-cpp.md)。

下列範例會產生 C3828，並示範如何修正此問題：

```
// C3828a.cpp
// compile with: /clr
ref struct M {
};

ref struct N {
   static array<char>^ bytes = gcnew array<char>(256);
};

int main() {
   M ^m1 = new (&N::bytes) M();   // C3828
   // The following line fixes the error.
   // M ^m1 = gcnew M();
}
```
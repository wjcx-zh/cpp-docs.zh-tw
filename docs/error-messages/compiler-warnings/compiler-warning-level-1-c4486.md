---
title: 編譯器警告（層級1） C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 4c92c23af4aeb6a18c812517cfef9fa00d15dfcb
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965398"
---
# <a name="compiler-warning-level-1-c4486"></a>編譯器警告（層級1） C4486

' function '： ref 類別或實值類別的私用虛擬方法應該標記為 ' sealed '

由於 managed 類別或結構的私用虛擬成員函式無法存取或覆寫，因此它應該標記為[sealed](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4486。

```cpp
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>範例

下列範例顯示私用密封的虛擬函式的其中一種可能用法。

```cpp
// C4486_b.cpp
// compile with: /clr /c
ref class B {};

ref class D : B {};

interface class I {
   B^ mf();
};

ref class E : I {
private:
   virtual B^ g() sealed = I::mf {
      return gcnew B;
   }

public:
   virtual D^ mf() {
      return gcnew D;
   }
};
```
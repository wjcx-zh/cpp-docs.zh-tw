---
title: 編譯器警告 (層級 1) C4486
ms.date: 11/04/2016
f1_keywords:
- C4486
helpviewer_keywords:
- C4486
ms.assetid: 2c0c59e3-d025-4d97-8da2-fa27df1402fc
ms.openlocfilehash: 402d5eefde6c2dfd5693e53c27edb00d1ac2e56c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779189"
---
# <a name="compiler-warning-level-1-c4486"></a>編譯器警告 (層級 1) C4486

'function': ref 類別或實值類別的私用虛擬方法標記為 'sealed'

因為無法存取或覆寫的受管理的類別或結構的私用虛擬成員函式，應該標示[密封](../../extensions/sealed-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C4486。

```
// C4486.cpp
// compile with: /clr /c /W1
ref class B {
private:
   virtual void f() {}   // C4486
   virtual void f1() sealed {}   // OK
};
```

## <a name="example"></a>範例

下列範例示範可能用法之一私人密封虛擬函式。

```
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
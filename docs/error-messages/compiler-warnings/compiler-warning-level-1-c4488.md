---
title: 編譯器警告 (層級 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: c816c1b3f5481ccff19fd2a2377c5fc98f950fee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404074"
---
# <a name="compiler-warning-level-1-c4488"></a>編譯器警告 (層級 1) C4488

'function': 需要 'keyword' 關鍵字，來實作介面方法 'interface_method'

類別必須實作它直接繼承的介面中的所有成員。 實作的成員必須具有公用存取範圍，並必須標示為虛擬。

## <a name="example"></a>範例

如果實作的成員不是公用，則可能會發生 C4488。 下列範例會產生 C4488。

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>範例

如果實作的成員未標記為 virtual，可能會發生 C4488。 下列範例會產生 C4488。

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```
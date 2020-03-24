---
title: 編譯器警告 (層級 1) C4488
ms.date: 11/04/2016
f1_keywords:
- C4488
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
ms.openlocfilehash: b83845f0ed0efeee6485780c7e4f828e40473e9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186695"
---
# <a name="compiler-warning-level-1-c4488"></a>編譯器警告 (層級 1) C4488

' function '：需要 ' 關鍵字 ' 關鍵字來執行介面方法 ' interface_method '

類別必須執行其直接繼承之介面的所有成員。 實作為實成員必須具有公用存取範圍，而且必須標記為 virtual。

## <a name="example"></a>範例

如果實的成員不是公用的，則可能會發生 C4488。 下列範例會產生 C4488。

```cpp
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

如果已執行的成員未標記為 virtual，則可能會發生 C4488。 下列範例會產生 C4488。

```cpp
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```

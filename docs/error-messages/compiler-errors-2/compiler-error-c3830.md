---
title: 編譯器錯誤 C3830
ms.date: 11/04/2016
f1_keywords:
- C3830
helpviewer_keywords:
- C3830
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
ms.openlocfilehash: 25f2b86e21d4672c9e0907c366da17072bafa183
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778679"
---
# <a name="compiler-error-c3830"></a>編譯器錯誤 C3830

'type1': 無法繼承自 'type2'，值類型只能繼承自介面類別

實值型別無法繼承的基底類別。  如需詳細資訊，請參閱 <<c0> [ 類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3830:

```
// C3830a.cpp
// compile with: /clr /c
public value struct MyStruct4 {
   int i;
};

public value class MyClass : public MyStruct4 {};   // C3830

// OK
public interface struct MyInterface4 {
   void i();
};

public value class MyClass2 : public MyInterface4 {
public:
   virtual void i(){}
};
```

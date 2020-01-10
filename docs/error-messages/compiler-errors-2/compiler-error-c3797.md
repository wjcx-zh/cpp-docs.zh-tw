---
title: 編譯器錯誤 C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 7236cb75aef4250440a1e992415df07fb5b7da3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757172"
---
# <a name="compiler-error-c3797"></a>編譯器錯誤 C3797

' override '：事件宣告不能有覆寫規範（應該放在事件新增/移除/引發方法上）

您無法使用另一個一般事件來覆寫一般事件（沒有明確定義存取子方法的事件）。 覆寫事件必須定義其對存取子函式的行為。

如需詳細資訊，請參閱[事件](../../extensions/event-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3797。

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```

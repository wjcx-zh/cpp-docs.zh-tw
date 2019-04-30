---
title: 編譯器錯誤 C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 76206cdffce3f551ff472cbd83df486eb41ae80b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400132"
---
# <a name="compiler-error-c3797"></a>編譯器錯誤 C3797

'override': 事件宣告不能有覆寫規範 （應該置於事件新增/移除/引發方法改為）

您無法覆寫 trivial 事件 （不需要明確定義的存取子方法的事件） 與另一個 trivial 事件。 覆寫的事件必須定義其存取子函式的行為。

如需詳細資訊，請參閱 <<c0> [ 事件](../../extensions/event-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3797。

```
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
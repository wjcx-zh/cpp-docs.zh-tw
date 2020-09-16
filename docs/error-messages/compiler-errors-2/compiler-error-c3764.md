---
title: 編譯器錯誤 C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: d8cfcae544d0948c21e093ba6457159b0214a583
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685615"
---
# <a name="compiler-error-c3764"></a>編譯器錯誤 C3764

' override_function '：無法覆寫基類方法 ' base_class_function '

編譯器偵測到格式不正確的覆寫。 例如，基類函數不是 **`virtual`** 。 如需詳細資訊，請參閱覆 [寫](../../extensions/override-cpp-component-extensions.md)。

## <a name="examples"></a>範例

下列範例會產生 C3764。

```cpp
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

當基類方法同時明確且命名為覆寫時，也可能會發生 C3764。 下列範例會產生 C3764。

```cpp
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```

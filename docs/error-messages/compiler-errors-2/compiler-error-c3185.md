---
title: 編譯器錯誤 C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: db448b462cd3a3f325c529e730e5c8f65e2b8f51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598805"
---
# <a name="compiler-error-c3185"></a>編譯器錯誤 C3185

Managed 或 WinRT 類型 'type' 上使用 'typeid'，請改用 'operator'

您不能套用[typeid](../../cpp/typeid-operator.md)運算子，managed 或 WinRT 類型; 請改用[typeid](../../windows/typeid-cpp-component-extensions.md)改。

下列範例會產生 C3185，並示範如何修正此問題：

```
// C3185a.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};

int main() {
   Derived ^ pd = gcnew Derived;
   Base ^pb = pd;
   const type_info & t1 = typeid(pb);   // C3185
   System::Type ^ MyType = Base::typeid;   // OK
};
```

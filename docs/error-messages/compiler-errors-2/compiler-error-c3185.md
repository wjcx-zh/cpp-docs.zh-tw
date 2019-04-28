---
title: 編譯器錯誤 C3185
ms.date: 11/04/2016
f1_keywords:
- C3185
helpviewer_keywords:
- C3185
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
ms.openlocfilehash: 45afe70b454f72dd8c9b8ce9771ce1f5aef6a10e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366078"
---
# <a name="compiler-error-c3185"></a>編譯器錯誤 C3185

Managed 或 WinRT 類型 'type' 上使用 'typeid'，請改用 'operator'

您不能套用[typeid](../../cpp/typeid-operator.md)運算子，managed 或 WinRT 類型; 請改用[typeid](../../extensions/typeid-cpp-component-extensions.md)改。

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

---
title: 編譯器錯誤 C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 5bf4e2e42b4534d47a2a7d3c9a838c404a99ba68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328876"
---
# <a name="compiler-error-c3379"></a>編譯器錯誤 C3379

'class': 巢狀的類別不能有組件存取規範，其宣告的一部分

套用至受管理的類型，例如類別或結構時[公用](../../cpp/public-cpp.md)並[私人](../../cpp/private-cpp.md)關鍵字會指出是否將透過組件中繼資料中公開的類別。 `public` 或`private`無法套用至巢狀類別，將會繼承在封入類別的組件存取權。

搭配使用時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，則`ref`並`value`關鍵字會指出類別 managed (請參閱[類別和結構](../../extensions/classes-and-structs-cpp-component-extensions.md))。

下列範例會產生 C3379:

```
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```

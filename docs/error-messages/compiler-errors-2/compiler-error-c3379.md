---
title: 編譯器錯誤 C3379 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90a4ccc17e63c21d4b6fb26e607450849f27b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109323"
---
# <a name="compiler-error-c3379"></a>編譯器錯誤 C3379

'class': 巢狀的類別不能有組件存取規範，其宣告的一部分

套用至受管理的類型，例如類別或結構時[公用](../../cpp/public-cpp.md)並[私人](../../cpp/private-cpp.md)關鍵字會指出是否將透過組件中繼資料中公開的類別。 `public` 或`private`無法套用至巢狀類別，將會繼承在封入類別的組件存取權。

搭配使用時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)，則`ref`並`value`關鍵字會指出類別 managed (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))。

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

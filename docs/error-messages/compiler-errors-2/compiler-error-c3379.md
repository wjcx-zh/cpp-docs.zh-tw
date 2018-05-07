---
title: 編譯器錯誤 C3379 |Microsoft 文件
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
ms.openlocfilehash: 1ded7ebfba6ab9f9120ebfa48c1942209a74e704
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3379"></a>編譯器錯誤 C3379
'class': 巢狀的類別不能有當做其宣告的一部分的組件存取規範  
  
 當套用至受管理的類型，例如類別或結構，[公用](../../cpp/public-cpp.md)和[私人](../../cpp/private-cpp.md)關鍵字會指出是否將透過組件中繼資料中公開的類別。 `public` 或`private`無法套用至巢狀類別，將會繼承在封入類別的組件存取權。  
  
 當搭配[/clr](../../build/reference/clr-common-language-runtime-compilation.md)、`ref`和`value`關鍵字會指出類別 managed (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
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

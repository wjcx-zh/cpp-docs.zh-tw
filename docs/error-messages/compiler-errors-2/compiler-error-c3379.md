---
title: "編譯器錯誤 C3379 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 16c62e48a0190096e04dc4ccf0c17ca66c2f4094
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3379"></a>編譯器錯誤 C3379
'class': 巢狀的類別不能有為其宣告的一部分的組件存取規範  
  
 當套用至受管理的類型，例如類別或結構，[公用](../../cpp/public-cpp.md)和[私人](../../cpp/private-cpp.md)關鍵字指出是否會透過組件中繼資料中公開的類別。 `public`或`private`無法套用至巢狀類別，將會繼承在封入類別的組件存取權。  
  
 搭配使用時[/clr](../../build/reference/clr-common-language-runtime-compilation.md)、`ref`和`value`關鍵字指出 managed 類別 (請參閱[類別和結構](../../windows/classes-and-structs-cpp-component-extensions.md))。  
  
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


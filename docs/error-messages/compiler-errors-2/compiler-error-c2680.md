---
title: "編譯器錯誤 C2680 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2680
dev_langs: C++
helpviewer_keywords: C2680
ms.assetid: d6f7129e-dd17-4661-b680-18d6b925b1cc
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f3a7d58aa7eb126392a0484ce28753c477d6137c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2680"></a>編譯器錯誤 C2680
'type': 無效的目標類型名稱  
  
 轉換成類型的指標或參考不被嘗試轉型運算子。 [Dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子可以只能用於指標或參考。  
  
 下列範例會產生 C2680:  
  
```  
// C2680.cpp  
// compile with: /c  
class A { virtual void f(); };  
class B : public A {};  
  
void g(B b) {  
   A a;  
   a = dynamic_cast<A>(b);   // C2680  target not a reference type  
   a = dynamic_cast<A&>(b);   // OK  
}  
```  
  
 未定義的目標時，也會發生 C2680:  
  
```  
// C2680b.cpp  
// compile with: /clr /c  
// C2680 expected  
using namespace System::Collections;  
  
// Delete the following line to resolve.  
ref class A;   // not defined  
  
// Uncomment the following line to resolve.  
// ref class A{};  
  
public ref class B : ArrayList {  
   property A^ C[int] {  
      A^ get(int index) {  
         return dynamic_cast<A^>(this->default::get(index));  
      }  
      void set(int index, A^ value) {  
         this->default::set(index, value);   
      }  
   }  
};  
```
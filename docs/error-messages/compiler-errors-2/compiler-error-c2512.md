---
title: "編譯器錯誤 C2512 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2512
dev_langs:
- C++
helpviewer_keywords:
- C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 63090bc7dac08aa87bcd68e77c076185176a7285
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2512"></a>編譯器錯誤 C2512
'identifier'：沒有適當的預設建構函式  
  
 沒有預設建構函式適用於指定的類別、結構或等位。 只有在未提供使用者定義的建構函式時，編譯器才會提供預設建構函式。  
  
 如果您提供的建構函式採用非 void 參數，而且您想要允許類別不用參數即可建立 - 例如，做為陣列的項目 - 您也必須提供預設建構函式。 預設建構函式可為具備所有參數之預設值的建構函式。  
  
 下列範例會產生 C2512，並示範如何修正此問題：  
  
```  
// C2512.cpp  
// C2512 expected  
struct B {  
   B (char *);  
   // Uncomment the following line to fix.  
   // B() {};  
};  
  
int main() {  
   B b;   
}  
```  
  
 下列範例將示範更細微的 C2512。 若要修正此錯誤，請重新排列程式碼，以在參考其建構函式之前定義類別：  
  
```  
// C2512b.cpp  
// compile with: /c  
struct S {  
   struct X;  
  
   void f() {  
      X *x = new X();   // C2512 X not defined yet  
   }  
  
};  
  
struct S::X {};  
  
struct T {  
   struct X;  
   void f();  
};  
  
struct T::X {};  
  
void T::f() {  
   X *x = new X();  
}  
```  
  
 預設建構包含 const 或參考資料成員的類別之呼叫也可能導致 C2512。 這些成員必須在建構函式初始設定式清單中初始化，該清單可防止編譯器產生預設建構函式。  
  
 下列範例會產生 C2512，並示範如何修正此問題：  
  
```  
// C2512c.cpp  
// Compile by using: cl /c /W3 C2512c.cpp  
struct S {  
   const int i_;  
   int &r_;   
};   
  
int SumS() {  
   const int ci = 7;  
   int ir = 42;  
  
   S s1; // C2512 - no default constructor available  
   S s2{ci, ir};  // Fix - initialize const and reference members   
   return s2.i_ + s2.r_;  
}  
```

---
title: "編譯器錯誤 C2678 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2678
dev_langs:
- C++
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
caps.latest.revision: 12
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
ms.openlocfilehash: ce8ee4a0b211bb90ed8f04184f2ac96962032436
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2678"></a>編譯器錯誤 C2678
二元 'operator'：未定義使用左方運算元類型 'type' 的運算子 (或是沒有可接受的轉換)  
  
 若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。  
  
## <a name="example"></a>範例  
 當左方運算元是 const 限定，而運算子定義成採用非 const 引數時，可能會發生 C2678。  
  
 下列範例會產生 C2678，並示範如何修正此問題：  
  
```  
// C2678a.cpp  
// Compile by using: cl /EHsc /W4 C2678a.cpp  
struct Combo {  
   int number;  
   char letter;  
};  
  
inline Combo& operator+=(Combo& lhs, int rhs) {  
   lhs.number += rhs;  
   return lhs;  
}  
  
int main() {  
   Combo const combo1{ 42, 'X' };  
   Combo combo2{ 13, 'Z' };  
  
   combo1 += 6; // C2678  
   combo2 += 9; // OK - operator+= matches non-const Combo  
}  
```  
  
## <a name="example"></a>範例  
 如果您沒有先 pin 原生成員，就在其上呼叫成員函式，也可能會發生 C2678。  
  
 下列範例會產生 C2678，並示範如何修正此問題。  
  
```  
// C2678.cpp  
// compile with: /clr /c  
struct S { int _a; };  
  
ref class C {  
public:  
   void M( S param ) {  
      test = param;   // C2678  
  
      // OK  
      pin_ptr<S> ptest = &test;  
      *ptest = param;  
   }  
   S test;  
};  
```  


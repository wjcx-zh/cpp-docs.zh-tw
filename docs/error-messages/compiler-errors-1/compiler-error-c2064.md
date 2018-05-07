---
title: 編譯器錯誤 C2064 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2064
dev_langs:
- C++
helpviewer_keywords:
- C2064
ms.assetid: 6cda05da-f437-4f50-9813-ae69538713a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3e5e21d7c33c84bb531b53c08aefbfce9dc7fd8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2064"></a>編譯器錯誤 C2064
詞彙不等於使用 N 引數的函式  
  
 透過運算式對函式進行呼叫。 運算式不等於使用所指定引數數目之函式的指標。  
  
 在此範例中，程式碼嘗試呼叫非函式做為函式。 下列範例會產生 C2064：  
  
```  
// C2064.cpp  
int i, j;  
char* p;  
void func() {  
   j = i();    // C2064, i is not a function  
   p();        // C2064, p doesn't point to a function  
}  
```  
  
 您必須從物件執行個體的內容呼叫非靜態成員函式的指標。 下列範例會產生 C2064，並顯示如何修正它。  
  
```  
// C2064b.cpp  
struct C {  
   void func1(){}  
   void func2(){}  
};  
  
typedef void (C::*pFunc)();  
  
int main() {  
   C c;  
   pFunc funcArray[2] = {&C::func1, &C::func2};  
   (funcArray[0])();    // C2064   
   (c.*funcArray[0])(); // OK - function called in instance context  
}  
  
```  
  
 在類別內，成員函式指標也必須指出呼叫物件內容。 下列範例會產生 C2064，並顯示如何修正它。  
  
```  
// C2064d.cpp  
// Compile by using: cl /c /W4 C2064d.cpp  
struct C {  
   typedef void (C::*pFunc)();  
   pFunc funcArray[2];  
   void func1(){}  
   void func2(){}  
   C() {  
      funcArray[0] = &C::func1;  
      funcArray[1] = &C::func2;  
   }  
   void func3() {  
      (funcArray[0])();   // C2064  
      (this->*funcArray[0])(); // OK - called in this instance context  
   }  
};  
```
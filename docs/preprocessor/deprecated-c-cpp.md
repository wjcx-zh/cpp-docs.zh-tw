---
title: "deprecated (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.deprecated"
  - "deprecated_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "deprecated pragma"
  - "Pragma, deprecated"
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# deprecated (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**deprecated** pragma 可讓您指出，在未來版本中可能不再支援或不應該再使用某個函式、類型或任何其他識別項。  
  
## 語法  
  
```  
  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## 備註  
 當編譯器遇到取代符號時，就會發出 [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。  
  
 您可以取代巨集名稱。  為巨集名稱加上引號，否則會發生巨集展開。  
  
 [deprecated](../cpp/deprecated-cpp.md) `__declspec` 修飾詞可讓您為特定形式的多載函式指定取代狀態。  
  
## 範例  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 下列範例將示範如何取代類別：  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
---
title: "__if_exists 陳述式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__if_exists_cpp"
  - "__if_exists"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__if_exists 關鍵字 [C++]"
  - "識別項, 測試是否存在"
  - "符號, 測試是否存在"
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __if_exists 陳述式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`__if_exists` 陳述式會測試指定識別項是否存在。  如果識別項存在，就會執行指定的陳述式區塊。  
  
## 語法  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`identifier`|要測試其是否存在的識別項。|  
|`statements`|如果 `identifier`  存在，會執行一個或多個陳述式。|  
  
## 備註  
  
> [!CAUTION]
>  為取得最可靠的結果，使用 `__if_exists` 陳述式時請遵循下列條件約束。  
  
-   只能將 `__if_exists` 陳述式套用至簡單類型，而不能套用於範本。  
  
-   將 `__if_exists` 陳述式套用至類別內外的識別項。  勿將 `__if_exists` 陳述式套用至區域變數。  
  
-   只在函式本體中使用 `__if_exists` 陳述式。  在函式的主體之外，`__if_exists` 陳述式只能測試完整定義的類型。  
  
-   當您對多載函式進行測試時，無法對特定形式的多載進行測試。  
  
 `__if_exists` 陳述式的補數是 [\_\_if\_not\_exists](../cpp/if-not-exists-statement.md) 陳述式。  
  
## 範例  
 請注意，這個範例會使用範本，但不建議這樣做。  
  
```  
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## Output  
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## 請參閱  
 [選擇陳述式](../cpp/selection-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)   
 [\_\_if\_not\_exists 陳述式](../cpp/if-not-exists-statement.md)
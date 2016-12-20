---
title: "typeid 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "typeid 運算子"
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typeid 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## 備註  
 `typeid` 運算子允許在執行階段判斷物件的類型。  
  
 `typeid` 的結果為 **const type\_info&**。  該值是 **type\_info** 物件的參考，並根據使用的 `typeid` 形式表示 *type\-id* 或 *expression* 的類型。  如需詳細資訊，請參閱 [type\_info 類別](../cpp/type-info-class.md)。  
  
 `typeid` 運算子無法搭配 Managed 類型 \(抽象宣告子或執行個體\) 使用，如需取得所指定類型之 <xref:System.Type> 的詳細資訊，請參閱 [typeid](../windows/typeid-cpp-component-extensions.md)。  
  
 `typeid` 運算子套用至多型類別類型的左值時，會在物件真正的類型無法透過提供的靜態資訊判斷的情況下進行執行階段檢查。  這類案例包括：  
  
-   類別的參考  
  
-   已透過 \* 取值的指標  
  
-   註標的指標 \(也就是 \[ \]\)。\(請注意，使用具有多型類型指標的註標通常並不安全\)。  
  
 如果 *expression* 指向基底類別類型，但是物件的類型實際上是衍生自該基底類別，則結果會是衍生類別的 **type\_info** 參考。  *expression* 必須指向多型類型 \(具有虛擬函式的類別\)。  否則，結果會是 *expression* 中所參考靜態類別的 **type\_info**。  此外，指標必須已取值，才會使用其指向的物件。  若沒有為指標取值，則結果會是指標的 **type\_info**，而不是它所指向的目標。  例如：  
  
```  
// expre_typeid_Operator.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <typeinfo.h>  
  
class Base {  
public:  
   virtual void vvfunc() {}  
};  
  
class Derived : public Base {};  
  
using namespace std;  
int main() {  
   Derived* pd = new Derived;  
   Base* pb = pd;  
   cout << typeid( pb ).name() << endl;   //prints "class Base *"  
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"  
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"  
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"  
   delete pd;  
}  
```  
  
 如果 *expression* 會為指標取值，而且該指標的值為零，則 **typeid** 會擲回 [bad\_typeid 例外狀況](../cpp/bad-typeid-exception.md)。  如果指標不是指向有效的物件，則會擲回 `__non_rtti_object` 例外狀況，表示嘗試分析觸發錯誤的 RTTI \(類似存取違規\)，因為物件由於某種原因而無效 \(不正確的指標或程式碼未使用 [\/GR](../build/reference/gr-enable-run-time-type-information.md) 進行編譯\)。  
  
 如果 *expression* 不是指標，也不是物件的基底類別參考，則結果會是 **type\_info** 參考，表示 *expression* 的靜態類型。  運算式的 *static type* 是指運算式的類型，也就是在編譯時期所知的類型。  評估運算式的靜態類型時，會忽略執行語意。  此外，在判斷運算式的靜態類型時，會盡可能忽略參考：  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid** 也可以在樣板中用來判斷樣板參數的類型：  
  
```  
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## 請參閱  
 [執行階段類型資訊](../cpp/run-time-type-information.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)
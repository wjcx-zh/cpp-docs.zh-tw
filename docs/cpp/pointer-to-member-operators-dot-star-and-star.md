---
title: "成員指標運算子：.* 和 -&gt;* | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - ".*"
  - "->*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".* 運算子"
  - "->* 運算子"
  - "運算式 [C++], 運算子"
  - "運算式 [C++], 指標"
  - "成員指標運算子"
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 成員指標運算子：.* 和 -&gt;*
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
  
      expression .* expression  
expression –>* expression  
```  
  
## 備註  
 成員指標運算子 .\* 和 –\>\* 會針對運算式左邊指定的物件傳回特定類別成員的值。右邊則必須指定類別的成員。以下範例會示範如何使用這些運算子：  
  
```  
// expre_Expressions_with_Pointer_Member_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
class Testpm {  
public:  
   void m_func1() { cout << "m_func1\n"; }  
   int m_num;  
};  
  
// Define derived types pmfn and pmd.  
// These types are pointers to members m_func1() and  
// m_num, respectively.  
void (Testpm::*pmfn)() = &Testpm::m_func1;  
int Testpm::*pmd = &Testpm::m_num;  
  
int main() {  
   Testpm ATestpm;  
   Testpm *pTestpm = new Testpm;  
  
// Access the member function  
   (ATestpm.*pmfn)();  
   (pTestpm->*pmfn)();   // Parentheses required since * binds  
                        // less tightly than the function call.  
  
// Access the member data  
   ATestpm.*pmd = 1;  
   pTestpm->*pmd = 2;  
  
   cout  << ATestpm.*pmd << endl  
         << pTestpm->*pmd << endl;  
   delete pTestpm;  
}  
```  
  
## Output  
  
```  
m_func1  
m_func1  
1  
2  
```  
  
 在上述範例中，成員 `pmfn` 的指標會在叫用成員函式 `m_func1` 時使用。  另一個成員 `pmd` 的指標會在存取 `m_num` 成員時使用。  
  
 二元運算子 .\* 會將其第一個運算元 \(該運算元必須是類別類型的物件\) 與其第二個運算元 \(該運算元必須是成員指標類型\) 結合。  
  
 二元運算子 –\>\* 會將其第一個運算元 \(該運算元必須是類別類型物件的指標\) 與其第二個運算元 \(該運算元必須是成員指標類型\) 結合。  
  
 在包含 .\* 運算子的運算式中，第一個運算元必須是第二個運算元中所指定成員指標本身所屬且可存取的類別類型，或是該類別所明確衍生且可存取的類型。  
  
 在包含 –\>\* 運算子的運算式中，第一個運算元必須是第二個運算元中所指定類型的「類別類型指標」類型，或者必須是該類別所明確衍生的類型。  
  
## 範例  
 以下列類別和程式碼片段為例：  
  
```  
// expre_Expressions_with_Pointer_Member_Operators2.cpp  
// C2440 expected  
class BaseClass {  
public:  
   BaseClass(); // Base class constructor.  
   void Func1();  
};  
  
// Declare a pointer to member function Func1.  
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;  
  
class Derived : public BaseClass {  
public:  
   Derived();  // Derived class constructor.  
   void Func2();  
};  
  
// Declare a pointer to member function Func2.  
void (Derived::*pmfnFunc2)() = &Derived::Func2;  
  
int main() {  
   BaseClass ABase;  
   Derived ADerived;  
  
   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.  
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to  
                           // access pointers to members of  
                           // derived classes.   
  
   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously  
                              // derived from BaseClass.   
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.  
}  
```  
  
 .\* 或 –\>\* 成員指標運算子的結果是成員指標的宣告中所指定類型的物件或函式。  因此，在上述範例中，`ADerived.*pmfnFunc1()` 運算式的結果會是傳回 void 的函式指標。  如果第二個運算元是左值，則這個結果會是左值。  
  
> [!NOTE]
>  如果其中一個成員指標運算子的結果是函式，則結果只能做為函式呼叫運算子的運算元使用。  
  
## 請參閱  
 [C\+\+ 運算子](../misc/cpp-operators.md)   
 [C\+\+ 運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
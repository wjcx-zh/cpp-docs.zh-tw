---
title: "成員指標運算子:。 * 和-&gt;* |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- .*
- ->*
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1dad74e99612df6ef868b4cd1f0b2ca5abb9c506
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="pointer-to-member-operators--and--gt"></a>成員指標運算子:。 * 和-&gt;*
## <a name="syntax"></a>語法  
  
```  
expression .* expression  
expression ->* expression  
```  
  
## <a name="remarks"></a>備註  
 成員指標運算子。 * and->\*，傳回指定運算式的左側的物件的特定類別成員的值。  右邊則必須指定類別的成員。  以下範例會示範如何使用這些運算子：  
  
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
  
## <a name="output"></a>輸出  
  
```  
m_func1  
m_func1  
1  
2  
```  
  
 在上述範例中，成員 `pmfn` 的指標會在叫用成員函式 `m_func1` 時使用。 另一個成員 `pmd` 的指標會在存取 `m_num` 成員時使用。  
  
 二元運算子 .* 會將其第一個運算元 (該運算元必須是類別類型的物件) 與其第二個運算元 (該運算元必須是成員指標類型) 結合。  
  
 二元運算子-> * 結合其第一個運算元必須是類別類型的物件的指標與第二個運算元必須是成員指標類型。  
  
 在包含 .* 運算子的運算式中，第一個運算元必須是第二個運算元中所指定成員指標本身所屬且可存取的類別類型，或是該類別所明確衍生且可存取的類型。  
  
 在運算式中包含-> * 運算子的第一個運算元必須類型的 「 類別類型指標 」 類型指定在第二個運算元，或它必須類型的明確衍生自該類別。  
  
## <a name="example"></a>範例  
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
  
 結果。 * 或->\*成員指標運算子是物件或函式的成員指標宣告中指定的型別。 因此，在上述範例中，`ADerived.*pmfnFunc1()` 運算式的結果會是傳回 void 的函式指標。 如果第二個運算元是左值，則這個結果會是左值。  
  
> [!NOTE]
>  如果其中一個成員指標運算子的結果是函式，則結果只能做為函式呼叫運算子的運算元使用。  
  
## <a name="see-also"></a>另請參閱  
 [C++ 內建運算子、優先順序和順序關聯性](../cpp/cpp-built-in-operators-precedence-and-associativity.md)



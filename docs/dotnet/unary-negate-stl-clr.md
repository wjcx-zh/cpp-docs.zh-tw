---
title: "unary_negate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::unary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_negate 函式 [STL/CLR]"
ms.assetid: 83bbdd86-199c-4451-9f70-72f9ade2264a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# unary_negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述，呼叫時，會傳回其儲存的引數功能的邏輯否定的功能\)。  您會用它來指定函式物件根據其儲存的運算元。  
  
## 語法  
  
```  
template<typename Fun>  
    ref class unary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::argument_type argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    unary_negate(Fun% functor);  
    unary_negate(unary_negate<Fun>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Fun  
 儲存功能子型別。  
  
## 成員函式  
  
|類型定義|說明|  
|----------|--------|  
|argument\_type \- 型別引數|運算元引數的型別。|  
|委派型別|泛型委派的型別。|  
|結果型別|運算元結果的類型。|  
  
|成員|說明|  
|--------|--------|  
|unary\_negate|建構函式中。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|計算所需的函式。|  
|委派型別^|轉換子功能給委派。|  
  
## 備註  
 樣板類別描述中另一個引數功能讓另一個引數的功能。  它定義成員運算子 `operator()` ，如此一來，當物件，當做函式呼叫時，它會傳回儲存功能的邏輯 NOT 呼叫引數。  
  
 您也可以透過物件，因為型別為 `delegate_type^` 的函式引數，它會正確轉換。  
  
## 範例  
  
```  
// cliext_unary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(0);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 0"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::logical_not<int> not_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::unary_negate<cliext::logical_not<int> >(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        cliext::not1(not_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 0**  
 **1 0**  
 **1 0**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [not1](../dotnet/not1-stl-clr.md)
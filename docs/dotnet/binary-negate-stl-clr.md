---
title: "binary_negate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_negate 函式 [STL/CLR]"
ms.assetid: 0c3b47eb-0f37-4cb2-b879-4c9f0e57d275
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binary_negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述，呼叫時，會傳回其儲存的雙引數功能的邏輯否定的功能。  您會用它來指定函式物件根據其儲存的運算元。  
  
## 語法  
  
```  
template<typename Fun>  
    ref class binary_negate  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    explicit binary_negate(Fun% functor);  
    binary_negate(binary_negate<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Fun  
 儲存功能子型別。  
  
## 成員函式  
  
|型別定義|說明|  
|----------|--------|  
|delegate\_type|泛型委派的型別。|  
|first\_argument\_type|功能子的第一個引數的型別。|  
|result\_type|功能子結果的型別。|  
|second\_argument\_type|功能子的第二個引數的型別。|  
|stored\_function\_type|功能子的型別。|  
  
|成員|說明|  
|--------|--------|  
|binary\_negate|建構功能子。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|Computes the desired function.|  
|運算子 delegate\_type^\(\)|轉換功能子給委派。|  
  
## 備註  
 樣板類別描述中另一個雙引數功能讓雙另一個引數的功能。  它定義成員運算子 `operator()` ，如此一來，當物件當做函式呼叫時，它會傳回儲存功能的邏輯 NOT 呼叫雙引數。  
  
 您也可以將物件當作型別為 `delegate_type^` 的函式引數來傳遞，它會適當地轉換。  
  
## 範例  
  
```  
// cliext_binary_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(4);   
    c2.push_back(4);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 4 4"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::less<int> less_op;   
  
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(),   
        cliext::binary_negate<cliext::less<int> >(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::not2(less_op));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **4 4**  
 **1 0**  
 **1 0**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [not2](../dotnet/not2-stl-clr.md)
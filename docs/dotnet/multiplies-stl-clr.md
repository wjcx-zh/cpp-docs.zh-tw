---
title: "multiplies (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiplies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multiplies 函式 [STL/CLR]"
ms.assetid: 76d23149-789a-48a1-89f8-9103df82a1df
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# multiplies (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

範例類別描述當一個函式被呼叫，會傳回第一個引數乘以第二的功能。  您可用它來根據引數型別指定函式物件。  
  
## 語法  
  
```  
template<typename Arg>  
    ref class multiplies  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    multiplies();  
    multiplies(multiplies<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Arg  
 引數和傳回值的型別。  
  
## 成員函式  
  
|型別定義|說明|  
|----------|--------|  
|delegate\_type|泛型委派的型別。|  
|first\_argument\_type|功能子的第一個引數的型別。|  
|result\_type|功能子結果的型別。|  
|second\_argument\_type|功能子的第二個引數的型別。|  
  
|成員|說明|  
|--------|--------|  
|multiplies|建構功能子。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|計算所需的函式。|  
|operator delegate\_type^|轉換功能子給委派。|  
  
## 備註  
 這個樣板類別描述兩個引數的功能子。  它定義成員運算子 `operator()` ，如此一來，當物件被當做函式呼叫時，會傳回第一個引數乘以第二個。  
  
 您也可以將物件當作型別為 `delegate_type^` 的函式引數來傳遞，它會適當地轉換。  
  
## 範例  
  
```  
// cliext_multiplies.cpp   
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
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::multiplies<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **2 1**  
 **8 3**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [divides](../dotnet/divides-stl-clr.md)   
 [模數](../dotnet/modulus-stl-clr.md)
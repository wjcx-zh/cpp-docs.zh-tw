---
title: "binder2nd (STL/CLR) | Microsoft Docs"
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
  - "cliext::binder2nd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder2nd 函式 [STL/CLR]"
ms.assetid: f4be8722-1778-4cb9-9ec7-ad1443f6899f
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binder2nd (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述，呼叫時，會傳回，其儲存的兩個引數呼叫的功能與提供的第一個引數和其儲存的第二個引數的單一引數功能\)。  您會用它來指定函式物件根據其儲存的功能\)。  
  
## 語法  
  
```  
template<typename Fun>  
    ref class binder2nd  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        first_argument_type, result_type>  
        delegate_type;  
  
    binder2nd(Fun% functor, second_argument_type left);  
    binder2nd(binder2nd<Arg>% right);  
  
    result_type operator()(first_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 有趣。  
 儲存功能子型別。  
  
## 成員函式  
  
|型別定義|說明|  
|----------|--------|  
|delegate\_type|泛型委派的型別。|  
|first\_argument\_type|功能的第一個引數的型別。|  
|result\_type|功能的結果的型別。|  
|second\_argument\_type|功能的第二個引數的型別。|  
|stored\_function\_type|功能的類型。|  
  
|成員|說明|  
|--------|--------|  
|binder2nd|建構函式中。|  
  
|運算子|說明|  
|---------|--------|  
|運算子 \(\)|計算所需的函式。|  
|運算子 delegate\_type^\(\)|轉換子功能給委派。|  
  
## 備註  
 樣板類別描述儲存兩個引數功能和第二個引數的單一引數功能\)。  它定義成員運算子 `operator()` ，如此一來，當物件，當做函式呼叫時，它會呼叫與提供的第一個引數和儲存的第二個引數的儲存功能\) 的結果。  
  
 您也可以透過物件，因為型別為 `delegate_type^` 的函式引數，它會正確轉換。  
  
## 範例  
  
```  
// cliext_binder2nd.cpp   
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
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **0 \-1**  
 **0 \-1**   
## 需求  
 **標題:** \<cliext\/功能\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [bind2nd](../dotnet/bind2nd-stl-clr.md)
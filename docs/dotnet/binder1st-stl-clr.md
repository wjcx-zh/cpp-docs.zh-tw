---
title: "binder1st (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binder1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder1st 函式 [STL/CLR]"
ms.assetid: a989c9cc-a485-45d9-bd19-519018e6974b
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# binder1st (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述單一引數功能，當他呼叫時，會傳回與第一個引數一同呼叫的已儲存兩個引數功能和提供的第二個引數。  您會用它來指定函式物件根據其儲存的運算元。  
  
## 語法  
  
```  
template<typename Fun>  
    ref class binder1st  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        second_argument_type, result_type>  
        delegate_type;  
  
    binder1st(Fun% functor, first_argument_type left);  
    binder1st(binder1st<Arg>% right);  
  
    result_type operator()(second_argument_type right);  
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
|binder1st|建構功能子。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|計算所需的函式。|  
|運算子 delegate\_type^\(\)|轉換功能子給委派。|  
  
## 備註  
 樣板類別描述儲存雙引數功能的一個引數及第一個引數。  它定義成員運算子 `operator()` ，如此一來，當物件做函式呼叫時，它會回傳已儲存的功能及已儲存的第一個引數和提供的第二個引數的呼叫結果。  
  
 您也可以將物件當作型別為 `delegate_type^` 的函式引數來傳遞，它會適當地轉換。  
  
## 範例  
  
```  
// cliext_binder1st.cpp   
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
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **\-1 0**  
 **\-1 0**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [bind1st](../dotnet/bind1st-stl-clr.md)
---
title: "less (STL/CLR) | Microsoft Docs"
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
  - "cliext::less"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less 函式 [STL/CLR]"
ms.assetid: fae56216-af66-4cb9-a688-be58a7c7edbb
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# less (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別，描述，當呼叫，傳回 true 的功能時，只有第一個引數小於第二個。  您會用它來指定函式物件根據其引數型別。  
  
## 語法  
  
```  
template<typename Arg>  
    ref class less  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    less();  
    less(less<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Arg  
 引數的型別。  
  
## 成員函式  
  
|型別定義|說明|  
|----------|--------|  
|delegate\_type|泛型委派的型別。|  
|first\_argument\_type|功能的第一個引數的型別。|  
|result\_type|功能的結果的型別。|  
|second\_argument\_type|功能的第二個引數的型別。|  
  
|成員|說明|  
|--------|--------|  
|less|建構函式中。|  
  
|運算子|說明|  
|---------|--------|  
|運算子 \(\)|計算所需的函式。|  
|運算子 delegate\_type^|轉換子功能給委派。|  
  
## 備註  
 樣板類別會描述兩個引數的功能。  它定義成員運算子 `operator()` ，如此一來，當物件，當做函式呼叫時，它會傳回 true，表示只在第一個引數小於第二個。  
  
 您也可以透過物件，因為型別為 `delegate_type^` 的函式引數，它會正確轉換。  
  
## 範例  
  
```  
// cliext_less.cpp   
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
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::less<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **4 4**  
 **0 1**   
## 需求  
 **標題:** \<cliext\/功能\>  
  
 **命名空間:** cliext  
  
## 請參閱  
 [greater\_equal](../dotnet/greater-equal-stl-clr.md)
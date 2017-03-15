---
title: "greater_equal (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::greater_equal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "greater_equal 函式 [STL/CLR]"
ms.assetid: 4d4d8301-72dd-4a06-a652-5237e1e72a88
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# greater_equal (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別，描述，當呼叫，傳回 true 的功能，表示只在第一個引數大於或等於第二個。  您會用它來指定函式物件根據其引數型別。  
  
## 語法  
  
```  
template<typename Arg>  
    ref class greater_equal  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    greater_equal();  
    greater_equal(greater_equal<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Arg  
 引數型別。  
  
## 成員函式  
  
|類型定義|說明|  
|----------|--------|  
|委派型別|泛型委派的型別。|  
|第一個引數類型。|功能的第一個引數的型別。|  
|結果型別|運算元結果的類型。|  
|第二個引數類型。|運算元第二個引數的型別。|  
  
|成員|說明|  
|--------|--------|  
|greater\_equal|建構運算元。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|計算所需的函式。|  
|運算子 delegate\_type^|轉換子功能給委派。|  
  
## 備註  
 樣板類別會描述兩個引數的功能。  它定義成員運算子 `operator()` ，如此一來，當物件，當做函式呼叫時，它會傳回 true，表示只在第一個引數大於或等於第二個。  
  
 您也可以透過物件，因為型別為 `delegate_type^` 的函式引數，它會正確轉換。  
  
## 範例  
  
```  
// cliext_greater_equal.cpp   
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
        c2.begin(), c3.begin(), cliext::greater_equal<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **4 4**  
 **1 0**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [less](../dotnet/less-stl-clr.md)
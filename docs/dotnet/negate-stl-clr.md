---
title: "negate (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate 函式 [STL/CLR]"
ms.assetid: 58e4c339-0dee-4db8-b2cc-de8920977039
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別描述呼叫時會傳回它的相反引數的功能。  您可用它來根據引數型別指定函式物件。  
  
## 語法  
  
```  
template<typename Arg>  
    ref class negate  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    negate();  
    negate(negate<Arg>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### 參數  
 Arg  
 引數的型別。  
  
## 成員函式  
  
|型別定義|說明|  
|----------|--------|  
|argument\_type|功能子引數的型別。|  
|delegate\_type|泛型委派的型別。|  
|result\_type|功能子結果的型別。|  
  
|成員|說明|  
|--------|--------|  
|negate|建構功能子。|  
  
|運算子|說明|  
|---------|--------|  
|operator\(\)|計算所需的函式。|  
|operator delegate\_type^|轉換功能子給委派。|  
  
## 備註  
 這個樣板類別描述單一引數的功能子。  它定義成員運算子 `operator()` ，如此一來，當物件當做函式呼叫時，它會傳回其相反的引數。  
  
 您也可以將物件當作型別為 `delegate_type^` 的函式引數來傳遞，它會適當地轉換。  
  
## 範例  
  
```  
// cliext_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(-3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 -3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::negate<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 \-3**  
 **\-4 3**   
## 需求  
 **標頭：** \<cliext\/functional\>  
  
 **命名空間：** cliext  
  
## 請參閱  
 [logical\_not](../dotnet/logical-not-stl-clr.md)
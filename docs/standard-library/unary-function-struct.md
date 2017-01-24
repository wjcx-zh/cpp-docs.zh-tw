---
title: "unary_function 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unary_function"
  - "unary_function"
  - "functional/std::unary_function"
  - "std::unary_function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_function 類別"
ms.assetid: 04c2fbdc-c1f6-48ed-b6cc-292a6d484627
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unary_function 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義型別可能會由衍生類別繼承提供一元運算的函式物件的空的基礎結構。  
  
## 語法  
  
```  
  
   template<class Arg, class Result>  
struct unary_function {  
   typedef Arg argument_type;  
   typedef Result result_type;  
};  
```  
  
## 備註  
 範本結構做為的基底對於定義表單 **result\_type** `operator()`的類別 \(**const**\)**argument\_type&const**的 10% 成員函式。  
  
 所有這類衍生的一元的函式中參考其單一引數型別， **argument\_type** 和其傳回型別為 **result\_type**。  
  
## 範例  
  
```  
// functional_unary_function.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
// Creation of a user-defined function object  
// that inherits from the unary_function base class  
class greaterthan10: unary_function<int, bool>  
{  
public:  
    result_type operator()(argument_type i)  
    {  
        return (result_type)(i > 10);  
    }  
};  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( " ;  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(), greaterthan10());  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
}  
```  
  
  **The vector v1 \= \( 0 5 10 15 20 25 \)**  
**項目數目 v1 大於 10 的是:3.**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [unary\_function\<\> 結構](../misc/unary-function-angles-structure.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)
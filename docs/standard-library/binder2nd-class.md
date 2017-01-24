---
title: "binder2nd 類別 | Microsoft Docs"
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
  - "std.binder2nd"
  - "binder2nd"
  - "xfunctional/std::binder2nd"
  - "std::binder2nd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder2nd 類別"
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
caps.latest.revision: 22
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# binder2nd 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供一個建構函式的樣板類別，此建構函式透過繫結二元函式第二個引數為指定值，將二元函式物件轉換為一元函式物件。  
  
## 語法  
  
```  
template<class Operation>  
   class binder2nd  
      : public unary_function <  
         typename Operation::first_argument_type,  
         typename Operation::result_type>   
   {  
   public:  
   typedef typename Operation::argument_type argument_type;  
   typedef typename Operation::result_type result_type;  
   binder2nd(  
      const Operation& _Func,  
      const typename Operation::second_argument_type& _Right  
   );  
   result_type operator()(  
      const argument_type& _Left  
   ) const;  
   result_type operator()(  
      argument_type& _Left  
   ) const;  
   protected:  
   Operation op;  
   typename Operation::second_argument_type value;  
   };  
```  
  
#### 參數  
 `_Func`  
 要轉換的二元函式物件對一元的函式物件。  
  
 `_Right`  
 二元函式物件的第二個引數所繫結的值。  
  
 `_Left`  
 引數的值符合的二進位物件與第二個引數的不可變值比較。  
  
## 傳回值  
 一元的函式物件從繫結的結果二元函式物件的第二個引數值的 `_Right.`。  
  
## 備註  
 樣板類別在 **op**存放二進位函式物件 \_Func 複本和 `_Right` 複製到 **value**的。  它會定義成員的函式 `operator()` 為傳回 **op**`_Left`， \( **value**\)。  
  
 如果 `_Func` 屬於型別 **Operation** 物件，並為常數，則 [bind2nd](../Topic/bind2nd%20Function.md) \( `_Func`， `c` \) 與 `binder2nd` 類別建構函式 `binder2nd`\<**Operation**\> \( `_Func`\)， `c` 等於且更方便。  
  
## 範例  
  
```  
// functional_binder2nd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(),  
        binder2nd<greater<int> >(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare using binder1st fixing 1st argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder1st<greater<int> >(greater<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
  **The vector v1 \= \( 0 5 10 15 20 25 \)**  
**項目數目 v1 大於 10 的是:3.**  
**項目數目 v1 小於 10 的是:2.**   
## 需求  
 **標題:** \<functional\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [標準樣板程式庫](../misc/standard-template-library.md)
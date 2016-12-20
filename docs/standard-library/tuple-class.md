---
title: "tuple 類別 | Microsoft Docs"
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
  - "tr1::tuple"
  - "std.tr1.tuple"
  - "tuple"
  - "tr1.tuple"
  - "std::tr1::tuple"
  - "tuple/std::tr1::tuple"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple 類別"
  - "tuple 類別 [TR1]"
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
caps.latest.revision: 19
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tuple 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包裝項目固定長度的序列。  
  
## 語法  
  
```  
template<class T1, class T2, ..., class TN>  
class tuple {  
public:  
    tuple();  
    explicit tuple(P1, P2, ..., PN);              // 0 < N  
    tuple(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple(const pair<U1, U2>&);               // N == 2  
    void swap(tuple& right);  
    tuple& operator=(const tuple&);  
    template <class U1, class U2, ..., class UN>  
        tuple& operator=(const tuple<U1, U2, ..., UN>&);  
    template <class U1, class U2>  
        tuple& operator=(const pair<U1, U2>&);    // N == 2  
    };  
```  
  
#### 參數  
 `TN`  
 第 n 個 Tuple 項目的型別。  
  
## 備註  
 樣板類別描述儲存型別 `T1`， `T2`的物件\)，…， `TN`，分別，其中 `0 <= N <= Nmax`的位置。  Tuple 執行個體 `tuple<T1, T2, ..., TN>` 的範圍是其樣板引數數目 `N` 。  樣板引數的 `Ti` 索引和該型別的對應儲存的值是 `i - 1`。  因此，反之，我們從 1 編號型別加入至文件的 N，從 0 到 1 \- N. 的對應索引值的範圍。  
  
## 範例  
  
```  
// tuple.cpp  
// compile with: /EHsc  
  
#include <vector>  
#include <iomanip>  
#include <iostream>  
#include <tuple>  
#include <string>  
  
using namespace std;  
  
typedef tuple <int, double, string> ids;  
  
void print_ids(const ids& i)  
{  
   cout << "( "  
        << get<0>(i) << ", "   
        << get<1>(i) << ", "   
        << get<2>(i) << " )." << endl;  
}  
  
int main( )  
{  
   // Using the constructor to declare and initialize a tuple  
   ids p1(10, 1.1e-2, "one");  
  
   // Compare using the helper function to declare and initialize a tuple  
   ids p2;  
   p2 = make_tuple(10, 2.22e-1, "two");  
  
   // Making a copy of a tuple  
   ids p3(p1);  
  
   cout.precision(3);  
   cout << "The tuple p1 is: ( ";  
   print_ids(p1);  
   cout << "The tuple p2 is: ( ";  
   print_ids(p2);  
   cout << "The tuple p3 is: ( ";  
   print_ids(p3);  
  
   vector<ids> v;  
  
   v.push_back(p1);  
   v.push_back(p2);  
   v.push_back(make_tuple(3, 3.3e-2, "three"));  
  
   cout << "The tuples in the vector are" << endl;  
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)  
   {  
      print_ids(*i);  
   }  
}  
```  
  
  **Tuple p1 如下:\(10， 0.011，一個\)。**  
**Tuple p2 如下:\(10， 0.222，兩個\)。**  
**Tuple p3 如下:\(10， 0.011，一個\)。**  
**向量中的 Tuple。**  
**\(10， 0.011，一個\)。**  
**\(10， 0.222，兩個\)。**  
**\(3， 0.033，三個\)。**   
## 需求  
 **標題:** \<Tuple\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<tuple\>](../standard-library/tuple.md)   
 [make\_tuple 函式](../Topic/make_tuple%20Function.md)
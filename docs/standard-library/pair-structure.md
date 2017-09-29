---
title: "pair 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- utility/std::pair
dev_langs:
- C++
helpviewer_keywords:
- pair class
ms.assetid: 539d3d67-80a2-4170-b347-783495d42109
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: e8884eb598002d6dbf3e4bc310d163658afc249b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/27/2017

---
# <a name="pair-structure"></a>pair 結構
提供可將兩個物件視為單一物件之功能的結構。  
  
## <a name="syntax"></a>語法  
```  
struct pair
{
    typedef T1 first_type;
    typedef T2 second_type;
    T1 first;
    T2 second;
    constexpr pair();
    constexpr pair(
        const T1& Val1,
        const T2& Val2);

    template <class Other1, class Other2>
    constexpr pair(const pair<Other1, Other2>& Right);

    template <class Other1, class Other2>
    constexpr pair(const pair <Other1 Val1, Other2 Val2>&& Right);

    template <class Other1, class Other2>
    constexpr pair(Other1&& Val1, Other2&& Val2);
};
```  
#### <a name="parameters"></a>參數  
 `Val1`  
 值，初始化 `pair` 第一個項目。  
  
 `Val2`  
 值，初始化 `pair` 第二個項目。  
  
 `Right`  
 配對，其值要用來初始化另一個配對的項目。  
  
## <a name="return-value"></a>傳回值  
 第一個 (預設) 建構函式會初始化此配對的第一個項目為 **T1** 類型的預設值，並且將第二個項目初始化為 **T2** 類型的預設值。  
  
 第二個建構函式會初始化該配對的第一個項目為 `Val1`，並且將第二個項目初始化為 *Val2*。  
  
 第三個 (範本) 建構函式會初始化該配對的第一個項目為 `Right`. **first** 和第二個項目為 `Right`. **second**。  
  
 第四個建構函式會使用[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)，初始化該配對的第一個項目為 `Val1`，並且將第二個項目初始化為 *Val2*。  
  
## <a name="remarks"></a>備註  
 範本結構會分別儲存一組 **T1** 和 **T2** 類型物件的配對。 類型 **first_type** 等同於範本參數 **T1**，而類型 **second_type** 等同於範本參數 **T2**。 **T1** 和 **T2** 各自只需要提供預設建構函式、單一引數建構函式和解構函式。 類型 `pair` 的所有成員是公用的，因為該類型宣告為 `struct`，而不是 **class**。 配對最常見的兩種用途是當作函式的傳回類型，這些函式會傳回兩個值，以及當作關聯容器類別 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)的項目，這些類別都具有與每個項目相關聯的索引鍵和實值類型。 後者滿足成對關聯容器的需求，也具有 `pair`< **const**`key_type`, `mapped_type`> 形式的實值類型。  
  
## <a name="example"></a>範例  
  
```cpp  
// utility_pair.cpp  
// compile with: /EHsc  
#include <utility>  
#include <map>  
#include <iomanip>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
  
   // Using the constructor to declare and initialize a pair  
   pair <int, double> p1 ( 10, 1.1e-2 );  
  
   // Compare using the helper function to declare and initialize a pair  
   pair <int, double> p2;  
   p2 = make_pair ( 10, 2.22e-1 );  
  
   // Making a copy of a pair  
   pair <int, double> p3 ( p1 );  
  
   cout.precision ( 3 );  
   cout << "The pair p1 is: ( " << p1.first << ", "   
        << p1.second << " )." << endl;  
   cout << "The pair p2 is: ( " << p2.first << ", "   
        << p2.second << " )." << endl;  
   cout << "The pair p3 is: ( " << p3.first << ", "   
        << p3.second << " )." << endl;  
  
   // Using a pair for a map element  
   map <int, int> m1;  
   map <int, int>::iterator m1_Iter;  
  
   typedef pair <int, int> Map_Int_Pair;  
  
   m1.insert ( Map_Int_Pair ( 1, 10 ) );  
   m1.insert ( Map_Int_Pair ( 2, 20 ) );  
   m1.insert ( Map_Int_Pair ( 3, 30 ) );  
  
   cout << "The element pairs of the map m1 are:";  
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )  
      cout << " ( " << m1_Iter -> first << ", "  
           << m1_Iter -> second << " )";  
   cout   << "." << endl;  
  
   // Using pair as a return type for a function  
   pair< map<int,int>::iterator, bool > pr1, pr2;  
   pr1 = m1.insert ( Map_Int_Pair ( 4, 40 ) );  
   pr2 = m1.insert ( Map_Int_Pair (1, 10 ) );  
  
   if( pr1.second == true )  
   {  
      cout << "The element (4,40) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr1.first) -> first ) = " << ( pr1.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
  
   if( pr2.second == true )  
   {  
      cout << "The element (1,10) was inserted successfully in m1."  
           << endl;  
   }  
   else     
   {  
      cout << "The element with a key value of\n"  
           << " ( (pr2.first) -> first ) = " << ( pr2.first ) -> first   
           << " is already in m1,\n so the insertion failed." << endl;  
   }  
}  
\* Output:   
The pair p1 is: ( 10, 0.011 ).  
The pair p2 is: ( 10, 0.222 ).  
The pair p3 is: ( 10, 0.011 ).  
The element pairs of the map m1 are: ( 1, 10 ) ( 2, 20 ) ( 3, 30 ).  
The element (4,40) was inserted successfully in m1.  
The element with a key value of  
 ( (pr2.first) -> first ) = 1 is already in m1,  
 so the insertion failed.  
*\  
```  
  
## <a name="requirements"></a>需求  
 **標頭：**\<utility>  
  
 **命名空間：** std  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)





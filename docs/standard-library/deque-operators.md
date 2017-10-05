---
title: "&lt;deque&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
dev_langs:
- C++
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 81645c8f645a3c3a09ef641b2fce003260bcd5f6
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 測試運算子左邊的 deque 物件是否不等於右邊的 deque 物件。  
  
```
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果 deque 物件不相等，則為 **true**；如果 deque 物件相等，則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 如果有相同數目的元素，且個別元素擁有相同的值，則兩個 deque 物件相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_ne.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c2.push_back( 2 );  
  
   if ( c1 != c2 )  
      cout << "The deques are not equal." << endl;  
   else  
      cout << "The deques are equal." << endl;  
}  
\* Output:   
The deques are not equal.  
*\  
```  
  
##  <a name="op_lt"></a>  operator&lt;  
 測試運算子左邊的 deque 物件是否小於右邊的 deque 物件。  
  
```
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的 deque 小於且不等於右邊的 deque，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_lt.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 < c2 )  
      cout << "Deque c1 is less than deque c2." << endl;  
   else  
      cout << "Deque c1 is not less than deque c2." << endl;  
}  
\* Output:   
Deque c1 is less than deque c2.  
*\   
```  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
 測試運算子左邊的 deque 物件是否小於或等於右邊的 deque 物件。  
  
```
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的 deque 小於或等於右邊的 deque，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於或等於關聯性，是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_le.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 <= c2 )  
      cout << "Deque c1 is less than or equal to deque c2." << endl;  
   else  
      cout << "Deque c1 is greater than deque c2." << endl;  
}  
\* Output:   
Deque c1 is less than or equal to deque c2.  
*\  
  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 測試運算子左邊的 deque 物件是否等於右邊的 deque 物件。  
  
```
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的 deque 等於右邊的 deque，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 如果有相同數目的元素，且個別元素擁有相同的值，則兩個 deque 相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_eq.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c2.push_back( 1 );  
  
   if ( c1 == c2 )  
      cout << "The deques are equal." << endl;  
   else  
      cout << "The deques are not equal." << endl;  
  
   c1.push_back( 1 );  
   if ( c1 == c2 )  
      cout << "The deques are equal." << endl;  
   else  
      cout << "The deques are not equal." << endl;  
}  
\* Output:   
The deques are equal.  
The deques are not equal.  
*\  
  
```  
  
##  <a name="op_gt"></a>  operator&gt;  
 測試運算子左邊的 deque 物件是否大於右邊的 deque 物件。  
  
```
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的 deque 大於右邊的 deque，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_gt.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 > c2 )  
      cout << "Deque c1 is greater than deque c2." << endl;  
   else  
      cout << "Deque c1 is not greater than deque c2." << endl;  
}  
\* Output:   
Deque c1 is greater than deque c2.  
*\  
  
```  
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
 測試運算子左邊的 deque 物件是否大於或等於右邊的 deque 物件。  
  
```
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `deque` 類型的物件。  
  
 `right`  
 `deque` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的 deque 大於或等於右邊的 deque，即為 **true**；否則為 **false**。  
  
### <a name="remarks"></a>備註  
 deque 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於或等於關聯性，是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// deque_op_ge.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2;  
  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 >= c2 )  
      cout << "Deque c1 is greater than or equal to deque c2." << endl;  
   else  
      cout << "Deque c1 is less than deque c2." << endl;  
}  
\* Output:   
Deque c1 is greater than or equal to deque c2.  
*\  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<deque>](../standard-library/deque.md)





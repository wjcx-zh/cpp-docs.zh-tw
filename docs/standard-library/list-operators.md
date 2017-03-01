---
title: "&lt;list&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 617ac2187ec3cd6d46cec6076fa72cc437803714
ms.lasthandoff: 02/24/2017

---
# <a name="ltlistgt-operators"></a>&lt;list&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 測試運算子左邊的清單物件是否不等於右邊的清單物件。  
  
```
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果清單不相等，便會傳回 **true**；如果清單相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 如果有相同數目的元素，且個別元素擁有相同的值，則兩個清單相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_ne.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )  
{  
using namespace std;  
list <int> c1, c2;  
c1.push_back( 1 );  
c2.push_back( 2 );  
  
if ( c1 != c2 )  
cout << "Lists not equal." << endl;  
else  
cout << "Lists equal." << endl;  
}  
\* Output:  
Lists not equal.  
*\  
```  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 測試運算子左邊的清單物件是否小於右邊的清單物件。  
  
```
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單小於但不等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_lt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 < c2 )  
      cout << "List c1 is less than list c2." << endl;  
   else  
      cout << "List c1 is not less than list c2." << endl;  
}  
\* Output:   
List c1 is less than list c2.  
*\   
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 測試運算子左邊的清單物件是否小於或等於右邊的清單物件。  
  
```
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單小於或等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於或等於關聯性，是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_le.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 4 );  
  
   c2.push_back( 1 );  
   c2.push_back( 3 );  
  
   if ( c1 <= c2 )  
      cout << "List c1 is less than or equal to list c2." << endl;  
   else  
      cout << "List c1 is greater than list c2." << endl;  
}  
\* Output:   
List c1 is less than or equal to list c2.  
*\  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 測試運算子左邊的清單物件是否等於右邊的清單物件。  
  
```
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 如果有相同數目的元素，且個別元素擁有相同的值，則兩個清單相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_eq.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
  
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c2.push_back( 1 );  
  
   if ( c1 == c2 )  
      cout << "The lists are equal." << endl;  
   else  
      cout << "The lists are not equal." << endl;  
}  
\* Output:   
The lists are equal.  
*\  
```  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 測試運算子左邊的清單物件是否大於右邊的清單物件。  
  
```
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單大於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_gt.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 > c2 )  
      cout << "List c1 is greater than list c2." << endl;  
   else  
      cout << "List c1 is not greater than list c2." << endl;  
}  
\* Output:   
List c1 is greater than list c2.  
*\  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 測試運算子左邊的清單物件是否大於或等於右邊的清單物件。  
  
```
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **list** 類型的物件。  
  
 `right`  
 **list** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的清單大於或等於運算子右邊的清單，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 list 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於或等於關聯性，是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// list_op_ge.cpp  
// compile with: /EHsc  
#include <list>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
   list <int> c1, c2;  
   c1.push_back( 1 );  
   c1.push_back( 3 );  
   c1.push_back( 1 );  
  
   c2.push_back( 1 );  
   c2.push_back( 2 );  
   c2.push_back( 2 );  
  
   if ( c1 >= c2 )  
      cout << "List c1 is greater than or equal to list c2." << endl;  
   else  
      cout << "List c1 is less than list c2." << endl;  
}  
\* Output:   
List c1 is greater than or equal to list c2.  
*\  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<list>](../standard-library/list.md)





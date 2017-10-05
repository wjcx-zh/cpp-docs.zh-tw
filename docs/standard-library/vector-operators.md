---
title: "&lt;vector&gt; 運算子| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
dev_langs:
- C++
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
caps.latest.revision: 13
manager: ghogen
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 310bf81e6dd20440c57ce5a0c73da7a6919f0015
ms.contentlocale: zh-tw
ms.lasthandoff: 10/03/2017

---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>  operator!=  
 測試運算子左邊的物件是否不等於右邊的物件。  
  
```  
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 如果向量不相等為 **true**；如果向量相等則為 **false**。  
  
### <a name="remarks"></a>備註  
 如果有相同數目的元素，且個別元素擁有相同的值，則兩個向量相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_ne.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
     v2.push_back( 2 );  
  
   if ( v1 != v2 )  
      cout << "Vectors not equal." << endl;  
   else  
      cout << "Vectors equal." << endl;  
}  
```  
  
```Output  
Vectors not equal.  
```  
  
##  <a name="op_lt"></a>  運算子&lt;  
 測試運算子左邊的物件是否小於右邊的物件。  
  
```  
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的向量小於運算子右邊的向量為 **true**；反之為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_lt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 < v2 )  
      cout << "Vector v1 is less than vector v2." << endl;  
   else  
      cout << "Vector v1 is not less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than vector v2.  
```  
  
##  <a name="op_lt_eq"></a>  運算子&lt;=  
 測試運算子左邊的物件是否小於或等於右邊的物件。  
  
```  
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的向量小於或等於右邊的向量為 **true**；反之為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_le.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   v1.push_back( 4 );  
  
   v2.push_back( 1 );  
   v2.push_back( 3 );  
  
   if ( v1 <= v2 )  
      cout << "Vector v1 is less than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is less than or equal to vector v2.  
```  
  
##  <a name="op_eq_eq"></a>  operator==  
 測試運算子左邊的物件是否等於右邊的物件。  
  
```  
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的向量等於右邊的向量為 **true**；反之為 **false**。  
  
### <a name="remarks"></a>備註  
 如果有相同數目的元素，且個別元素擁有相同的值，則兩個向量相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_eq.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v2.push_back( 1 );  
  
   if ( v1 == v2 )  
      cout << "Vectors equal." << endl;  
   else  
      cout << "Vectors not equal." << endl;  
}  
```  
  
```Output  
Vectors equal.  
```  
  
##  <a name="op_gt"></a>  運算子&gt;  
 測試運算子左邊的物件是否大於右邊的物件。  
  
```  
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的向量大於運算子右邊的向量為 **true**；反之為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_gt.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
   v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 > v2 )  
      cout << "Vector v1 is greater than vector v2." << endl;  
   else  
      cout << "Vector v1 is not greater than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than vector v2.  
```  
  
##  <a name="op_gt_eq"></a>  運算子&gt;=  
 測試運算子左邊的物件是否大於或等於右邊的物件。  
  
```  
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 類型 **vector** 的物件。  
  
 `right`  
 類型 **vector** 的物件。  
  
### <a name="return-value"></a>傳回值  
 若運算子左邊的向量大於或等於右邊的向量為 **true**；反之為 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// vector_op_ge.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;   
  
   vector <int> v1, v2;  
   v1.push_back( 1 );  
   v1.push_back( 3 );  
   v1.push_back( 1 );  
  
     v2.push_back( 1 );  
   v2.push_back( 2 );  
   v2.push_back( 2 );  
  
   if ( v1 >= v2 )  
      cout << "Vector v1 is greater than or equal to vector v2." << endl;  
   else  
      cout << "Vector v1 is less than vector v2." << endl;  
}  
```  
  
```Output  
Vector v1 is greater than or equal to vector v2.  
```  
  
## <a name="see-also"></a>另請參閱  
 [\<vector>](../standard-library/vector.md)



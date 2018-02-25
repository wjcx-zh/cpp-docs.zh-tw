---
title: "&lt;map&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
dev_langs:
- C++
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: d98e67ea5a65279a5bb618552bec4358bc48a445
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ltmapgt-operators"></a>&lt;map&gt; 運算子
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
|[operator!= (multimap)](#op_neq_multimap)|[operator&gt;](#op_gt_multimap)|[operator&gt;=](#op_gt_eq_multimap)|  
|[operator&lt;](#op_lt_multimap)|[operator&lt;=](#op_lt_eq_multimap)|[operator==](#op_eq_eq_multimap)|  
  
##  <a name="op_neq"></a> operator!=  
 測試運算子左邊的 map 物件是否不等於右邊的 map 物件。  
  
```
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果 map 不相等，便會傳回 **true**；如果 map 相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 map 物件之間的比較是以其元素的成對比較為基礎。 兩個 map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The maps m1 and m2 are not equal." << endl;  
   else  
      cout << "The maps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The maps m1 and m3 are not equal." << endl;  
   else  
      cout << "The maps m1 and m3 are equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_lt"></a> operator&lt;  
 測試運算子左邊的 map 物件是否小於右邊的 map 物件。  
  
```
bool operator<(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 map 絕對小於運算子右邊的 map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 map 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The map m1 is less than the map m2." << endl;  
   else  
      cout << "The map m1 is not less than the map m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The map m1 is less than the map m3." << endl;  
   else  
      cout << "The map m1 is not less than the map m3." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
The map m1 is not less than the map m3.  
*\  
```  
  
##  <a name="op_lt_eq"></a> operator&lt;=  
 測試運算子左邊的 map 物件是否小於或等於右邊的 map 物件。  
  
```
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 map 小於或等於運算子右邊的 map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "The map m1 is less than or equal to the map m2." << endl;  
   else  
      cout << "The map m1 is greater than the map m2." << endl;  
  
   if ( m1 <= m3 )  
      cout << "The map m1 is less than or equal to the map m3." << endl;  
   else  
      cout << "The map m1 is greater than the map m3." << endl;  
  
   if ( m1 <= m4 )  
      cout << "The map m1 is less than or equal to the map m4." << endl;  
   else  
      cout << "The map m1 is greater than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than or equal to the map m2.  
The map m1 is greater than the map m3.  
The map m1 is less than or equal to the map m4.  
*\  
```  
  
##  <a name="op_eq_eq"></a> operator==  
 測試運算子左邊的 map 物件是否等於右邊的 map 物件。  
  
```
bool operator==(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 map 等於運算子右邊的 map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 map 物件之間的比較是以其元素的成對比較為基礎。 兩個 map 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 == m2 )  
      cout << "The maps m1 and m2 are equal." << endl;  
   else  
      cout << "The maps m1 and m2 are not equal." << endl;  
  
   if ( m1 == m3 )  
      cout << "The maps m1 and m3 are equal." << endl;  
   else  
      cout << "The maps m1 and m3 are not equal." << endl;  
}  
\* Output:   
The maps m1 and m2 are not equal.  
The maps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_gt"></a> operator&gt;  
 測試運算子左邊的 map 物件是否大於右邊的 map 物件。  
  
```
bool operator>(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 map 大於運算子右邊的 map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 map 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The map m1 is greater than the map m2." << endl;  
   else  
      cout << "The map m1 is not greater than the map m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The map m1 is greater than the map m3." << endl;  
   else  
      cout << "The map m1 is not greater than the map m3." << endl;  
}  
\* Output:   
The map m1 is not greater than the map m2.  
The map m1 is greater than the map m3.  
*\  
```  
  
##  <a name="op_gt_eq"></a> operator&gt;=  
 測試運算子左邊的 map 物件是否大於或等於右邊的 map 物件。  
  
```
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left, 
      const map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 **map** 類型的物件。  
  
 `right`  
 **map** 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 map 大於或等於運算子右邊的 map，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// map_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   map < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "Map m1 is greater than or equal to map m2." << endl;  
   else  
      cout << "The map m1 is less than the map m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "Map m1 is greater than or equal to map m3." << endl;  
   else  
      cout << "The map m1 is less than the map m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "Map m1 is greater than or equal to map m4." << endl;  
   else  
      cout << "The map m1 is less than the map m4." << endl;  
}  
\* Output:   
The map m1 is less than the map m2.  
Map m1 is greater than or equal to map m3.  
Map m1 is greater than or equal to map m4.  
*\  
```  
  
##  <a name="op_neq_multimap"></a>  operator!= (multimap)  
 測試運算子左邊的 multimap 物件是否不等於右邊的 multimap 物件。  
  
```
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果 multimap 不相等，便會傳回 **true**；如果 multimap 相等，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_ne.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 != m2 )  
      cout << "The multimaps m1 and m2 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m2 are equal." << endl;  
  
   if ( m1 != m3 )  
      cout << "The multimaps m1 and m3 are not equal." << endl;  
   else  
      cout << "The multimaps m1 and m3 are equal." << endl;  
}  
\* Output:   
The multimaps m1 and m2 are not equal.  
The multimaps m1 and m3 are equal.  
*\  
```  
  
##  <a name="op_lt_multimap"></a> operator&lt;  
 測試運算子左邊的 multimap 物件是否小於右邊的 multimap 物件。  
  
```
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 multimap 絕對小於運算子右邊的 multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_lt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 < m2 )  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m2." << endl;  
  
   if ( m1 < m3 )  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not less than the multimap m3." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is not less than the multimap m3.  
*\  
```  
  
##  <a name="eq_multimap"></a> operator&lt;=  
 測試運算子左邊的 multimap 物件是否小於或等於右邊的 multimap 物件。  
  
```
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 multimap 小於或等於運算子右邊的 multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_le.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap <int, int> m1, m2, m3, m4;  
   int i;  
   typedef pair <int, int> Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 <= m2 )  
      cout << "m1 is less than or equal to m2" << endl;  
   else  
      cout << "m1 is greater than m2" << endl;  
  
   if ( m1 <= m3 )  
      cout << "m1 is less than or equal to m3" << endl;  
   else  
      cout << "m1 is greater than m3" << endl;  
  
   if ( m1 <= m4 )  
      cout << "m1 is less than or equal to m4" << endl;  
   else  
      cout << "m1 is greater than m4" << endl;  
}  
\* Output:   
m1 is less than or equal to m2  
m1 is greater than m3  
m1 is less than or equal to m4  
*\  
```  
  
##  <a name="op_eq_eq_multimap"></a> operator==  
 測試運算子左邊的 multimap 物件是否等於右邊的 multimap 物件。  
  
```
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 multimap 等於運算子右邊的 multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個 multimap 如果元素數目相同，且其個別元素的值也相同，兩者便相等。 反之則為不相等。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_eq.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap<int, int> m1, m2, m3;  
   int i;  
   typedef pair<int, int> Int_Pair;  
  
   for (i = 0; i < 3; i++)  
   {  
      m1.insert(Int_Pair(i, i));  
      m2.insert(Int_Pair(i, i*i));  
      m3.insert(Int_Pair(i, i));  
   }  
  
   if ( m1 == m2 )  
      cout << "m1 and m2 are equal" << endl;  
   else  
      cout << "m1 and m2 are not equal" << endl;  
  
   if ( m1 == m3 )  
      cout << "m1 and m3 are equal" << endl;  
   else  
      cout << "m1 and m3 are not equal" << endl;  
}  
\* Output:   
m1 and m2 are not equal  
m1 and m3 are equal  
*\  
```  
  
##  <a name="op_gt_multimap"></a> operator&gt;  
 測試運算子左邊的 multimap 物件是否大於右邊的 multimap 物件。  
  
```
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 multimap 大於運算子右邊的 multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 multimap 物件之間的比較是以其元素的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_gt.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
   }  
  
   if ( m1 > m2 )  
      cout << "The multimap m1 is greater than the multimap m2." << endl;  
   else  
      cout << "Multimap m1 is not greater than multimap m2." << endl;  
  
   if ( m1 > m3 )  
      cout << "The multimap m1 is greater than the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is not greater than the multimap m3." << endl;  
}  
\* Output:   
Multimap m1 is not greater than multimap m2.  
The multimap m1 is greater than the multimap m3.  
*\  
```  
  
##  <a name="op_gt_eq_multimap"></a> operator&gt;=  
 測試運算子左邊的 multimap 物件是否大於或等於右邊的 multimap 物件。  
  
```
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left, 
      const multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>參數  
 `left`  
 `multimap` 類型的物件。  
  
 `right`  
 `multimap` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
 如果運算子左邊的 multimap 大於或等於運算子右邊的 multimap，便會傳回 **true**；否則會傳回 **false**。  
  
### <a name="example"></a>範例  
  
```cpp  
// multimap_op_ge.cpp  
// compile with: /EHsc  
#include <map>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multimap < int, int > m1, m2, m3, m4;  
   int i;  
   typedef pair < int, int > Int_Pair;  
  
   for ( i = 1 ; i < 3 ; i++ )  
   {  
      m1.insert ( Int_Pair ( i, i ) );  
      m2.insert ( Int_Pair ( i, i * i ) );  
      m3.insert ( Int_Pair ( i, i - 1 ) );  
      m4.insert ( Int_Pair ( i, i ) );  
   }  
  
   if ( m1 >= m2 )  
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m2." << endl;  
  
   if ( m1 >= m3 )  
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m3." << endl;  
  
   if ( m1 >= m4 )  
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;  
   else  
      cout << "The multimap m1 is less than the multimap m4." << endl;  
}  
\* Output:   
The multimap m1 is less than the multimap m2.  
The multimap m1 is greater than or equal to the multimap m3.  
The multimap m1 is greater than or equal to the multimap m4.  
*\  
```  
  
## <a name="see-also"></a>請參閱  
 [\<map>](../standard-library/map.md)




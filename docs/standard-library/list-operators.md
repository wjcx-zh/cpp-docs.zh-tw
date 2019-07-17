---
title: '&lt;list&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 7b0b7540c1b9a55140405a55e8e034f9c6ec646c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246455"
---
# <a name="ltlistgt-operators"></a>&lt;list&gt; 運算子

## <a name="op_neq"></a> 運算子 ！ =

測試運算子左邊的清單物件是否不等於右邊的清單物件。

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
Lists not equal.
*/
```

## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的清單物件是否小於右邊的清單物件。

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
List c1 is less than list c2.
*/
```

## <a name="op_lt_eq"></a> 運算子&lt;=

測試運算子左邊的清單物件是否小於或等於右邊的清單物件。

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="op_eq_eq"></a> 運算子 = =

測試運算子左邊的清單物件是否等於右邊的清單物件。

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
The lists are equal.
*/
```

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的清單物件是否大於右邊的清單物件。

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="op_gt_eq"></a> 運算子&gt;=

測試運算子左邊的清單物件是否大於或等於右邊的清單物件。

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左邊*\
`list` 類型的物件。

*權限*\
`list` 類型的物件。

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
/* Output:
List c1 is greater than or equal to list c2.
*/
```

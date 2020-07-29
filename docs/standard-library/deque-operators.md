---
title: '&lt;deque&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: d91fe64e7d06a80402a0a540be8f63d98ea96d37
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222481"
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; 運算子

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試運算子左邊的 deque 物件是否不等於右邊的 deque 物件。

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果 deque 物件不相等，則為，**`false`** 如果 deque 物件相等則為。

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
```

```Output
The deques are not equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試運算子左邊的 deque 物件是否小於右邊的 deque 物件。

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 deque 小於且不等於運算子右邊的 deque，則為，否則為。否則為 **`false`** 。

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
```

```Output
Deque c1 is less than deque c2.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的 deque 物件是否小於或等於右邊的 deque 物件。

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 deque 小於或等於運算子右邊的 deque，則為，否則為。否則為 **`false`** 。

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
```

```Output
Deque c1 is less than or equal to deque c2.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試運算子左邊的 deque 物件是否等於右邊的 deque 物件。

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 deque 等於運算子右邊的 deque，則為，否則為 **`false`** 。

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
```

```Output
The deques are equal.
The deques are not equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試運算子左邊的 deque 物件是否大於右邊的 deque 物件。

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 deque 大於運算子右邊的 deque，則為;否則為 **`false`** 。

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
```

```Output
Deque c1 is greater than deque c2.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的 deque 物件是否大於或等於右邊的 deque 物件。

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`deque` 類型的物件。

*再*\
`deque` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的 deque 大於或等於運算子右邊的 deque，則為，否則為。否則為 **`false`** 。

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
```

```Output
Deque c1 is greater than or equal to deque c2.
```

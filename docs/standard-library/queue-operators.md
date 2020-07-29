---
title: '&lt;queue&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- queue/std::operator!=
- queue/std::operator&gt;
- queue/std::operator&gt;=
- queue/std::operator&lt;
- queue/std::operator&lt;=
- queue/std::operator==
ms.assetid: 7c435b48-175c-45b0-88eb-24561044019c
helpviewer_keywords:
- std::operator!= (queue)
- std::operator&gt; (queue)
- std::operator&gt;= (queue)
- std::operator&lt; (queue)
- std::operator&lt;= (queue)
- std::operator== (queue)
ms.openlocfilehash: 8c02e79e6a300f23ac31ea876c9d4576cfe5e9a8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232920"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt; 運算子

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試運算子左邊的佇列物件是否不等於右邊的佇列物件。

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果佇列不相等，則為，**`false`** 如果佇列相等則為。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 如果有相同數目的項目，且個別項目擁有相同的值，則兩個佇列相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// queue_op_ne.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試運算子左邊的佇列物件是否小於右邊的佇列物件。

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的佇列小於且不等於運算子右邊的佇列，則為，否則為。否則為 **`false`** 。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 兩個佇列物件之間的小於關聯性是根據第一對不相等項目的比較。

### <a name="example"></a>範例

```cpp
// queue_op_lt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 < q2 )
      cout << "The queue q1 is less than the queue q2." << endl;
   else
      cout << "The queue q1 is not less than the queue q2." << endl;

   if ( q1 < q3 )
      cout << "The queue q1 is less than the queue q3." << endl;
   else
      cout << "The queue q1 is not less than the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is not less than the queue q3.
```

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的佇列物件是否小於或等於右邊的佇列物件。

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的佇列嚴格小於運算子右邊的佇列，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 兩個佇列物件之間的小於或等於關聯性，是根據第一對不相等項目的比較。

### <a name="example"></a>範例

```cpp
// queue_op_le.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 5 );
   q1.push( 10 );
   q2.push( 1 );
   q2.push( 2 );
   q3.push( 5 );
   q3.push( 10 );

   if ( q1 <= q2 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;

   if ( q1 <= q3 )
      cout << "The queue q1 is less than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is greater than the queue q2.
The queue q1 is less than or equal to the queue q3.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試運算子左邊的佇列物件是否等於右邊的佇列物件。

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果佇列不相等，則為，**`false`** 如果佇列相等則為。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 如果有相同數目的項目，且個別項目擁有相同的值，則兩個佇列相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// queue_op_eq.cpp
// compile with: /EHsc
#include <queue>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queues with list base containers
   queue <int, list<int> > q1, q2, q3;

   // The following line would have caused an error because vector
   // does not support pop_front( ) and so cannot be adapted
   // by queue as a base container
   // queue <int, vector<int> > q1, q2, q3;

   q1.push( 1 );
   q2.push( 2 );
   q3.push( 1 );

   if ( q1 != q2 )
      cout << "The queues q1 and q2 are not equal." << endl;
   else
      cout << "The queues q1 and q2 are equal." << endl;

   if ( q1 != q3 )
      cout << "The queues q1 and q3 are not equal." << endl;
   else
      cout << "The queues q1 and q3 are equal." << endl;
}
```

```Output
The queues q1 and q2 are not equal.
The queues q1 and q3 are equal.
```

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試運算子左邊的佇列物件是否大於右邊的佇列物件。

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的佇列嚴格小於運算子右邊的佇列，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 兩個佇列物件之間的大於關聯性是根據第一對不相等項目的比較。

### <a name="example"></a>範例

```cpp
// queue_op_gt.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q1.push( 3 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 > q2 )
      cout << "The queue q1 is greater than "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q2." << endl;

   if ( q1> q3 )
      cout << "The queue q1 is greater than "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is not greater than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is not greater than the queue q2.
The queue q1 is greater than the queue q3.
```

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的佇列物件是否大於或等於右邊的佇列物件。

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左面*\
`queue` 類型的物件。

*再*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的佇列嚴格小於運算子右邊的佇列，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

佇列物件之間的比較是以其項目的成對比較為基礎。 如果有相同數目的項目，且個別項目擁有相同的值，則兩個佇列相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// queue_op_ge.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2, q3;

   q1.push( 1 );
   q1.push( 2 );
   q2.push( 5 );
   q2.push( 10 );
   q3.push( 1 );
   q3.push( 2 );

   if ( q1 >= q2 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q2." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q2." << endl;

   if ( q1>= q3 )
      cout << "The queue q1 is greater than or equal to "
           << "the queue q3." << endl;
   else
      cout << "The queue q1 is less than "
           << "the queue q3." << endl;
}
```

```Output
The queue q1 is less than the queue q2.
The queue q1 is greater than or equal to the queue q3.
```

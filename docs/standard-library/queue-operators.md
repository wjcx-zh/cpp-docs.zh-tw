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
ms.openlocfilehash: 420d717b34b6c17587f8790701906e06ab008d96
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854883"
---
# <a name="ltqueuegt-operators"></a>&lt;queue&gt; 運算子

## <a name="op_neq"></a>operator！ =

測試運算子左邊的佇列物件是否不等於右邊的佇列物件。

```cpp
bool operator!=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

如果佇列不相等，則為 **true**；如果佇列相等，則為 **false**。

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

## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的佇列物件是否小於右邊的佇列物件。

```cpp
bool operator<(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

若運算子左邊的佇列小於且不等於運算子右邊的佇列，即為 **true**；否則為 **false**。

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

## <a name="op_lt_eq"></a>運算子&lt;=

測試運算子左邊的佇列物件是否小於或等於右邊的佇列物件。

```cpp
bool operator<=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左側的佇列必定小於運算子右側的佇列，則為 **true**；否則為 **false**。

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

## <a name="op_eq_eq"></a>operator = =

測試運算子左邊的佇列物件是否等於右邊的佇列物件。

```cpp
bool operator==(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

如果佇列不相等，則為 **true**；如果佇列相等，則為 **false**。

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

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的佇列物件是否大於右邊的佇列物件。

```cpp
bool operator>(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左側的佇列必定小於運算子右側的佇列，則為 **true**；否則為 **false**。

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

## <a name="op_gt_eq"></a>運算子&gt;=

測試運算子左邊的佇列物件是否大於或等於右邊的佇列物件。

```cpp
bool operator>=(const queue <Type, Container>& left, const queue <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`queue` 類型的物件。

*right*\
`queue` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左側的佇列必定小於運算子右側的佇列，則為 **true**；否則為 **false**。

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

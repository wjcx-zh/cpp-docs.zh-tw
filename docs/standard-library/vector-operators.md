---
title: '&lt;vector&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: 6e3b78a7b7176be917da5a3e44e9bf54efc0b08c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224535"
---
# <a name="ltvectorgt-operators"></a>&lt;vector&gt; 運算子

## <a name="operator"></a><a name="op_neq"></a>operator！ =

測試運算子左邊的物件是否不等於右邊的物件。

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果向量不相等，則為，**`false`** 如果向量相等則為。

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

## <a name="operatorlt"></a><a name="op_lt"></a>操作&lt;

測試運算子左邊的物件是否小於右邊的物件。

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的向量小於運算子右邊的向量，則為，否則為 **`false`** 。

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

## <a name="operatorlt"></a><a name="op_lt_eq"></a>操作&lt;=

測試運算子左邊的物件是否小於或等於右邊的物件。

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的向量小於或等於運算子右邊的向量，則為，否則為。否則為 **`false`** 。

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

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

測試運算子左邊的物件是否等於右邊的物件。

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的向量等於運算子右邊的向量，則為，否則為 **`false`** 。

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

## <a name="operatorgt"></a><a name="op_gt"></a>操作&gt;

測試運算子左邊的物件是否大於右邊的物件。

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的向量大於運算子右邊的向量，則為，否則為 **`false`** 。

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

## <a name="operatorgt"></a><a name="op_gt_eq"></a>操作&gt;=

測試運算子左邊的物件是否大於或等於右邊的物件。

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>參數

*左面*\
`vector` 類型的物件。

*再*\
`vector` 類型的物件。

### <a name="return-value"></a>傳回值

**`true`** 如果運算子左邊的向量大於或等於向量右側的向量，則為，否則為。否則為 **`false`** 。

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

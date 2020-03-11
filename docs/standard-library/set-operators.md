---
title: '&lt;set&gt; 運算子'
ms.date: 03/27/2019
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: 4618030cf81f79a085e16052c8b9c547201e3577
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875759"
---
# <a name="ltsetgt-operators"></a>&lt;set&gt; 運算子

## <a name="op_neq"></a>operator！ = （set）

測試運算子左邊的 set 物件是否不等於右邊的 set 物件。

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果 set 不相等，即為 **true**；如果 set 相等，則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目之間的成對比較為基礎。 如果兩個 set 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_lt"></a>運算子&lt; （set）

測試運算子左邊的 set 物件是否小於右邊的 set 物件。

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 set 必定小於運算子右邊的 set，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="op_lt_eq"></a>運算子&lt;= （set）

測試運算子左邊的 set 物件是否小於或等於右邊的 set 物件。

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 set 小於或等於運算子右邊的 set，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的小於或等於關聯性，是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
```

```Output
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
```

## <a name="op_eq_eq"></a>operator = = （set）

測試運算子左邊的 set 物件是否等於右邊的 set 物件。

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 set 等於運算子右邊的 set，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目的成對比較為基礎。 如果兩個 set 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
```

```Output
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
```

## <a name="op_gt"></a>運算子&gt; （set）

測試運算子左邊的 set 物件是否大於右邊的 set 物件。

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 set 大於運算子右邊的 set，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="op_gt_eq"></a>運算子&gt;= （set）

測試運算子左邊的 set 物件是否大於或等於右邊的 set 物件。

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`set` 類型的物件。

*right*\
`set` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 set 大於或等於清單右邊的 set，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

set 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的大於或等於關聯性，是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
```

```Output
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
```

## <a name="op_neq_multiset"></a>operator！ = （多重集）

測試運算子左邊的 multiset 物件是否不等於右邊的 multiset 物件。

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果 set 或 multiset 不相等，即為 **true**；如果 set 或 multiset 相等，則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目之間的成對比較為基礎。 如果兩個 set 或 multiset 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_lt_multiset"></a>運算子&lt; （多重集）

測試運算子左邊的 multiset 物件是否小於右邊的 multiset 物件。

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 multiset 絕對小於運算子右邊的 multiset，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的小於關聯性是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
```

## <a name="op_lt_eq_multiset"></a>運算子&lt;= （多重集）

測試運算子左邊的 multiset 物件是否小於或等於右邊的 multiset 物件。

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 multiset 小於或等於運算子右邊的 multiset，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的小於或等於關聯性，是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
```

## <a name="op_eq_eq_multiset"></a>operator = = （多重集）

測試運算子左邊的 multiset 物件是否等於右邊的 multiset 物件。

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 multiset 等於運算子右邊的 multiset，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目的成對比較為基礎。 如果兩個 set 或 multiset 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
```

```Output
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
```

## <a name="op_gt_multiset"></a>運算子&gt; （多重集）

測試運算子左邊的 multiset 物件是否大於右邊的 multiset 物件。

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 multiset 大於運算子右邊的 multiset，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的大於關聯性是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
```

```Output
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
```

## <a name="op_gt_eq_multiset"></a>運算子&gt;= （多重集）

測試運算子左邊的 multiset 物件是否大於或等於右邊的 multiset 物件。

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左方*\
`multiset` 類型的物件。

*right*\
`multiset` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 multiset 大於或等於清單右邊的 multiset，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

multiset 物件之間的比較是以其項目的成對比較為基礎。 兩個物件之間的大於或等於關聯性，是根據第一對不相等元素的比較。

### <a name="example"></a>範例

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
```

```Output
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
```

---
title: '&lt;set&gt; 運算子 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
dev_langs:
- C++
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: adc817c92bfaa79422dacafd17e4b1706e5a1af8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965639"
---
# <a name="ltsetgt-operators"></a>&lt;set&gt; 運算子

||||
|-|-|-|
|[operator!= (set)](#op_neq)|[operator&gt; (set)](#op_gt)|[operator&gt;= (set)](#eq)|
|[operator&lt; (set)](#op_lt)|[operator&lt;= (set)](#eq)|[operator== (set)](#op_eq_eq)|
|[operator!= (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|

## <a name="op_neq"></a>  operator!= (set)

測試運算子左邊的 set 物件是否不等於右邊的 set 物件。

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_lt"></a>  operator&lt; (set)

測試運算子左邊的 set 物件是否小於右邊的 set 物件。

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*\
```

## <a name="op_lt_eq"></a>  operator&lt;= (set)

測試運算子左邊的 set 物件是否小於或等於右邊的 set 物件。

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
*\
```

## <a name="op_eq_eq"></a>  operator== (set)

測試運算子左邊的 set 物件是否等於右邊的 set 物件。

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*\
```

## <a name="op_gt"></a>  operator&gt; (set)

測試運算子左邊的 set 物件是否大於右邊的 set 物件。

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*\
```

## <a name="op_gt_eq"></a>  operator&gt;= (set)

測試運算子左邊的 set 物件是否大於或等於右邊的 set 物件。

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`set`。

*右*型別的物件`set`。

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
\* Output:
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
*\
```

## <a name="op_neq_multiset"></a>  operator!= (multiset)

測試運算子左邊的 multiset 物件是否不等於右邊的 multiset 物件。

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_lt_multiset"></a>  operator&lt; (multiset)

測試運算子左邊的 multiset 物件是否小於右邊的 multiset 物件。

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
*\
```

## <a name="op_lt_eq_multiset"></a>  operator&lt;= (multiset)

測試運算子左邊的 multiset 物件是否小於或等於右邊的 multiset 物件。

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
*\
```

## <a name="op_eq_eq_multiset"></a>  operator== (multiset)

測試運算子左邊的 multiset 物件是否等於右邊的 multiset 物件。

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*\
```

## <a name="op_gt_multiset"></a>  operator&gt; (multiset)

測試運算子左邊的 multiset 物件是否大於右邊的 multiset 物件。

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
*\
```

## <a name="op_gt_eq_multiset"></a>  operator&gt;= (multiset)

測試運算子左邊的 multiset 物件是否大於或等於右邊的 multiset 物件。

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>參數

*左*型別的物件`multiset`。

*右*型別的物件`multiset`。

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
\* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
*\
```

## <a name="see-also"></a>另請參閱

[\<set>](../standard-library/set.md)<br/>

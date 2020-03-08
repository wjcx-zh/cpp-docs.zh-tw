---
title: '&lt;stack&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- stack/std::operator!=
- stack/std::operator&gt;
- stack/std::operator&gt;=
- stack/std::operator&lt;
- stack/std::operator&lt;=
- stack/std::operator==
ms.assetid: 9c1fc282-2f61-4727-9e80-84ea5d4934a2
helpviewer_keywords:
- std::operator!= (stack)
- std::operator&gt; (stack)
- std::operator&gt;= (stack)
- std::operator&lt; (stack)
- std::operator&lt;= (stack)
- std::operator== (stack)
ms.openlocfilehash: 169698d30edd4a7995cb05e1909c1ffc38b0b6ef
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865895"
---
# <a name="ltstackgt-operators"></a>&lt;stack&gt; 運算子

## <a name="op_neq"></a>operator！ =

測試運算子左邊的 stack 物件是否不等於右邊的 stack 物件。

```cpp
bool operator!=(const stack <Type, Container>& left, const stack <Type, Container>& right,);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

如果 stack 不相等，即為 **true**；如果 stack 相等，則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 如果兩個 stack 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// stack_op_me.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> >  s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 != s2 )
      cout << "The stacks s1 and s2 are not equal." << endl;
   else
      cout << "The stacks s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The stacks s1 and s3 are not equal." << endl;
   else
      cout << "The stacks s1 and s3 are equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_lt"></a> 運算子&lt;

測試運算子左邊的堆疊物件是否小於右邊的堆疊物件。

```cpp
bool operator<(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

若運算子左邊的 stack 小於且不等於右邊的 stack，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 兩個 stack 物件之間的小於關聯性，是以第一對不相等項目的比較為根據。

### <a name="example"></a>範例

```cpp
// stack_op_lt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 2 );
   s1.push( 4 );
   s1.push( 6 );
   s1.push( 8 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 2 );
   s3.push( 4 );
   s3.push( 6 );
   s3.push( 8 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;

   // to print out the stack s1 ( by unstacking the elements):
   stack <int>::size_type i_size_s1 = s1.size( );
   cout << "The stack s1 from the top down is: ( ";
   unsigned int i;
   for ( i = 1 ; i <= i_size_s1 ; i++ )
   {
      cout << s1.top( ) << " ";
      s1.pop( );
   }
   cout << ")." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
The stack s1 from the top down is: ( 8 6 4 2 ).
```

## <a name="op_lt_eq"></a>運算子&lt;=

測試運算子左邊的堆疊物件是否小於或等於右邊的堆疊物件。

```cpp
bool operator<=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

若運算子左邊的 stack 小於或等於右邊的 stack，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 兩個 stack 物件之間的小於或等於關聯性，是以第一對不相等項目的比較為根據。

### <a name="example"></a>範例

```cpp
// stack_op_le.cpp
// compile with: /EHsc
#include <stack>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with default deque base container
   stack <int> s1, s2, s3;

   s1.push( 5 );
   s1.push( 10 );
   s2.push( 1 );
   s2.push( 2 );
   s3.push( 5 );
   s3.push( 10 );

   if ( s1 <= s2 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;

   if ( s1 <= s3 )
      cout << "The stack s1 is less than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is greater than the stack s2.
The stack s1 is less than or equal to the stack s3.
```

## <a name="op_eq_eq"></a>operator = =

測試運算子左邊的 stack 物件是否等於右邊的 stack 物件。

```cpp
bool operator==(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

如果 stack 相等，即為 **true**；如果 stack 不相等，則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 如果兩個 stack 具有相同的項目數，且其個別項目的值相同，則它們會相等。 反之則為不相等。

### <a name="example"></a>範例

```cpp
// stack_op_eq.cpp
// compile with: /EHsc
#include <stack>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with vector base containers
   stack <int, vector<int> > s1, s2, s3;

   // The following would have cause an error because stacks with
   // different base containers are not equality comparable
   // stack <int, list<int> > s3;

   s1.push( 1 );
   s2.push( 2 );
   s3.push( 1 );

   if ( s1 == s2 )
      cout << "The stacks s1 and s2 are equal." << endl;
   else
      cout << "The stacks s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The stacks s1 and s3 are equal." << endl;
   else
      cout << "The stacks s1 and s3 are not equal." << endl;
}
```

```Output
The stacks s1 and s2 are not equal.
The stacks s1 and s3 are equal.
```

## <a name="op_gt"></a> 運算子&gt;

測試運算子左邊的堆疊物件是否大於右邊的堆疊物件。

```cpp
bool operator>(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

若運算子左邊的 stack 大於且不等於右邊的 stack，即為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 兩個 stack 物件之間的大於關聯性，是以第一對不相等項目的比較為根據。

### <a name="example"></a>範例

```cpp
// stack_op_gt.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s1.push( 3 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 > s2 )
      cout << "The stack s1 is greater than "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s2." << endl;

   if ( s1> s3 )
      cout << "The stack s1 is greater than "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is not greater than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is not greater than the stack s2.
The stack s1 is greater than the stack s3.
```

## <a name="op_gt_eq"></a>運算子&gt;=

測試運算子左邊的堆疊物件是否大於或等於右邊的堆疊物件。

```cpp
bool operator>=(const stack <Type, Container>& left, const stack <Type, Container>& right);
```

### <a name="parameters"></a>參數

*左方*\
`stack` 類型的物件。

*right*\
`stack` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算子左邊的 stack 必定小於運算子右邊的 stack，即為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

stack 物件之間的比較是以其項目的成對比較為基礎。 兩個 stack 物件之間的大於或等於關聯性，是以第一對不相等項目的比較為根據。

### <a name="example"></a>範例

```cpp
// stack_op_ge.cpp
// compile with: /EHsc
#include <stack>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares stacks with list base container
   stack <int, list<int> > s1, s2, s3;

   s1.push( 1 );
   s1.push( 2 );
   s2.push( 5 );
   s2.push( 10 );
   s3.push( 1 );
   s3.push( 2 );

   if ( s1 >= s2 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s2." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s2." << endl;

   if ( s1>= s3 )
      cout << "The stack s1 is greater than or equal to "
           << "the stack s3." << endl;
   else
      cout << "The stack s1 is less than "
           << "the stack s3." << endl;
}
```

```Output
The stack s1 is less than the stack s2.
The stack s1 is greater than or equal to the stack s3.
```

---
title: '&lt;iterator&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::operator!=
- xutility/std::operator&gt;
- xutility/std::operator&gt;=
- xutility/std::operator&lt;
- xutility/std::operator&lt;=
- xutility/std::operator+
- xutility/std::operator-
- xutility/std::operator==
ms.assetid: b7c664f0-49d4-4993-b5d1-9ac4859fdddc
helpviewer_keywords:
- std::operator!= (iterator)
- std::operator&gt; (iterator)
- std::operator&gt;= (iterator)
- std::operator&lt; (iterator)
- std::operator&lt;= (iterator), std::operator== (iterator)
ms.openlocfilehash: 311710d5614bbc7c24d6b32e89285715476f94da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510795"
---
# <a name="ltiteratorgt-operators"></a>&lt;iterator&gt; 運算子

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator+](#op_add)|
|[operator-](#operator-)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

測試運算子左邊的迭代器物件是否不等於右邊的迭代器物件。

```cpp
template <class RandomIterator>
bool operator!=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);

template <class Type, class CharType, class Traits, class Distance>
bool operator!=(const istream_iterator<Type, CharType, Traits, Distance>& left, const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>
bool operator!=(const istreambuf_iterator<CharType, Traits>& left, const istreambuf_iterator<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`iterator` 類型的物件。

*right*<br/>
`iterator` 類型的物件。

### <a name="return-value"></a>傳回值

如果迭代器物件不相等，便會傳回 **true**；如果迭代器物件相等，則會傳回 **false**。

### <a name="remarks"></a>備註

一個迭代器物件與另一個迭代器物件如果定址對象是容器中的相同元素，兩者便相等。 如果兩個迭代器指向容器中不同的元素，它們便不相等。

### <a name="example"></a>範例

```cpp
// iterator_op_ne.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 9 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 != rVPOS2 )
      cout << "The iterators are not equal." << endl;
   else
      cout << "The iterators are equal." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 != rVPOS2 )
      cout << "The iterators are not equal." << endl;
   else
      cout << "The iterators are equal." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 4 5 6 7 8 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 8.
The iterators are equal.
The iterator rVPOS1 now points to the second element
in the reversed sequence: 7.
The iterators are not equal.
```

## <a name="op_eq_eq"></a> operator==

測試運算子左邊的迭代器物件是否等於右邊的迭代器物件。

```cpp
template <class RandomIterator1, class RandomIterator2>
bool operator==(
    const move_iterator<RandomIterator1>& left,
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>
bool operator==(
    const reverse_iterator<RandomIterator1>& left,
    const reverse_iterator<RandomIterator2>& right);

template <class Type, class CharType, class Traits, class Distance>
bool operator==(
    const istream_iterator<Type, CharType, Traits, Distance>& left,
    const istream_iterator<Type, CharType, Traits, Distance>& right);

template <class CharType, class Tr>
bool operator==(
    const istreambuf_iterator<CharType, Traits>& left,
    const istreambuf_iterator<CharType, Traits>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
iterator 類型的物件。

*right*<br/>
iterator 類型的物件。

### <a name="return-value"></a>傳回值

**true**迭代器物件是否相等;**false**迭代器物件是否不相等。

### <a name="remarks"></a>備註

一個迭代器物件與另一個迭代器物件如果定址對象是容器中的相同元素，兩者便相等。 如果兩個迭代器指向容器中不同的元素，它們便不相等。

第一次的兩個範本運算子會傳回則為 true，只有當這兩個*左*並*右*儲存相同的迭代器。 第三個範本運算子會傳回 true，只有當這兩個*左*並*右*儲存相同的資料流指標。 第四個範本運算子會傳回 ` left.equal ( right)`。

### <a name="example"></a>範例

```cpp
// iterator_op_eq.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 == rVPOS2 )
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   if ( rVPOS1 == rVPOS2 )
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
The iterators are equal.
The iterator rVPOS1 now points to the second element
in the reversed sequence: 8.
The iterators are not equal.
```

## <a name="op_lt"></a> operator&lt;

測試運算子左邊的迭代器物件是否小於右邊的迭代器物件。

```cpp
template <class RandomIterator>
bool operator<(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
`iterator` 類型的物件。

*right*<br/>
`iterator` 類型的物件。

### <a name="return-value"></a>傳回值

如果運算式左邊的迭代器小於運算式右邊的迭代器，便會傳回 **true**；如果大於或等於右邊的迭代器，則會傳回 **false**。

### <a name="remarks"></a>備註

一個迭代器物件所定址的元素在容器中如果位於另一個迭代器物件所定址的元素之前，前面的迭代器物件便小於後面的迭代器物件。 一個迭代器物件所定址的元素如果與另一個迭代器物件所定址的元素相同，或所定址的元素在容器中位於另一個迭代器物件所定址的元素之後，前面的迭代器物件便不小於後面的迭代器物件。

### <a name="example"></a>範例

```cpp
// iterator_op_lt.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1& rVPOS2 initially point to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 < rVPOS2 )
      cout << "The iterator rVPOS1 is less than"
              << " the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is not less than"
              << " the iterator rVPOS2." << endl;

   rVPOS2++;
   cout << "The iterator rVPOS2 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 < rVPOS2 )
      cout << "The iterator rVPOS1 is less than"
              << " the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is not less than"
              << " the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1& rVPOS2 initially point to the first element
in the reversed sequence: 10.
The iterator rVPOS1 is not less than the iterator rVPOS2.
The iterator rVPOS2 now points to the second element
in the reversed sequence: 8.
The iterator rVPOS1 is less than the iterator rVPOS2.
```

## <a name="op_lt_eq"></a> operator&lt;=

測試運算子左邊的迭代器物件是否小於或等於右邊的迭代器物件。

```cpp
template <class RandomIterator>
bool operator<=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
iterator 類型的物件。

*right*<br/>
iterator 類型的物件。

### <a name="return-value"></a>傳回值

如果運算式左邊的迭代器小於或等於運算式右邊的迭代器，便會傳回 **true**；如果大於右邊的迭代器，則會傳回 **false**。

### <a name="remarks"></a>備註

一個迭代器物件所定址的元素如果與另一個迭代器物件所定址的元素相同，或在容器中位於該元素之前，前面的迭代器物件便小於或等於後面的迭代器物件。 一個迭代器物件所定址的元素在容器中如果位於另一個迭代器物件所定址的元素之後，前面的迭代器物件便大於後面的迭代器物件。

### <a name="example"></a>範例

```cpp
// iterator_op_le.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ) + 1,
           rVPOS2 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the "
           << "second element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   cout << "The iterator rVPOS2 initially points to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 <= rVPOS2 )
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;

   rVPOS2++;
   cout << "The iterator rVPOS2 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 <= rVPOS2 )
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the second element
in the reversed sequence: 8.
The iterator rVPOS2 initially points to the first element
in the reversed sequence: 10.
The iterator rVPOS1 is greater than the iterator rVPOS2.
The iterator rVPOS2 now points to the second element
in the reversed sequence: 8.
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.
```

## <a name="op_gt"></a> operator&gt;

測試運算子左邊的迭代器物件是否大於右邊的迭代器物件。

```cpp
template <class RandomIterator>
bool operator>(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
iterator 類型的物件。

*right*<br/>
iterator 類型的物件。

### <a name="return-value"></a>傳回值

如果運算式左邊的迭代器大於運算式右邊的迭代器，便會傳回 **true**；如果小於或等於右邊的迭代器，則會傳回 **false**。

### <a name="remarks"></a>備註

一個迭代器物件所定址的元素在容器中如果位於另一個迭代器物件所定址的元素之後，前面的迭代器物件便大於後面的迭代器物件。 一個迭代器物件所定址的元素如果與另一個迭代器物件所定址的元素相同，或所定址的元素在容器中位於另一個迭代器物件所定址的元素之前，前面的迭代器物件便不大於後面的迭代器物件。

### <a name="example"></a>範例

```cpp
// iterator_op_gt.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1 & rVPOS2 initially point to "
           << "the first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 > rVPOS2 )
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 > rVPOS2 )
      cout << "The iterator rVPOS1 is greater than "
              << "the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than or "
              << "equal to the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1 & rVPOS2 initially point to the first element
in the reversed sequence: 10.
The iterator rVPOS1 is less than or equal to the iterator rVPOS2.
The iterator rVPOS1 now points to the second element
in the reversed sequence: 8.
The iterator rVPOS1 is greater than the iterator rVPOS2.
```

## <a name="op_gt_eq"></a> operator&gt;=

測試運算子左邊的迭代器物件是否大於或等於右邊的迭代器物件。

```cpp
template <class RandomIterator>
bool operator>=(const reverse_iterator<RandomIterator>& left, const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
iterator 類型的物件。

*right*<br/>
iterator 類型的物件。

### <a name="return-value"></a>傳回值

如果運算式左邊的迭代器大於或等於運算式右邊的迭代器，便會傳回 **true**；如果小於右邊的迭代器，則會傳回 **false**。

### <a name="remarks"></a>備註

一個迭代器物件所定址的元素如果與另一個迭代器物件所定址的元素相同，或在容器中位於該元素之後，前面的迭代器物件便大於或等於後面的迭代器物件。 一個迭代器物件所定址的元素在容器中如果位於另一個迭代器物件所定址的元素之前，前面的迭代器物件便小於後面的迭代器物件。

### <a name="example"></a>範例

```cpp
// iterator_op_ge.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
           rVPOS2 = vec.rbegin ( ) + 1;

   cout << "The iterator rVPOS1 initially points to the "
           << "first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   cout << "The iterator rVPOS2 initially points to the "
           << "second element\n in the reversed sequence: "
           << *rVPOS2 << "." << endl;

   if ( rVPOS1 >= rVPOS2 )
      cout << "The iterator rVPOS1 is greater than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than "
              << "the iterator rVPOS2." << endl;

   rVPOS1++;
   cout << "The iterator rVPOS1 now points to the second "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   if ( rVPOS1 >= rVPOS2 )
      cout << "The iterator rVPOS1 is greater than or "
              << "equal to the iterator rVPOS2." << endl;
   else
      cout << "The iterator rVPOS1 is less than "
              << "the iterator rVPOS2." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
The iterator rVPOS2 initially points to the second element
in the reversed sequence: 8.
The iterator rVPOS1 is less than the iterator rVPOS2.
The iterator rVPOS1 now points to the second element
in the reversed sequence: 8.
The iterator rVPOS1 is greater than or equal to the iterator rVPOS2.
```

## <a name="op_add"></a>  operator+

將位移新增至迭代器，並傳回定址對象是在新位移位置中插入之元素的 `move_iterator` 或 `reverse_iterator`。

```cpp
template <class RandomIterator, class Diff>
move_iterator<RandomIterator>
operator+(
    Diff _Off,
    const move_iterator<RandomIterator>& right);

template <class RandomIterator>
reverse_iterator<RandomIterator>
operator+(
    Diff _Off,
    const reverse_iterator<RandomIterator>& right);
```

### <a name="parameters"></a>參數

*_Off*<br/>
要為常數 move_iterator 或常數 reverse_iterator 調整位移的位置數目。

*right*<br/>
要調整位移的迭代器。

### <a name="return-value"></a>傳回值

傳回總和*右* + *_Off*。

### <a name="example"></a>範例

```cpp
// iterator_op_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )  {
      vec.push_back ( 2 * i );
      }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to "
           << "the first element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;

   vector<int>::difference_type diff = 4;
   rVPOS1 = diff +rVPOS1;

   cout << "The iterator rVPOS1 now points to the fifth "
           << "element\n in the reversed sequence: "
           << *rVPOS1 << "." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
The iterator rVPOS1 now points to the fifth element
in the reversed sequence: 2.
```

## <a name="operator-"></a>  operator-

將一個迭代器減去另一個，並傳回差異。

```cpp
template <class RandomIterator1, class RandomIterator2>
Tdiff operator-(
    const move_iterator<RandomIterator1>& left,
    const move_iterator<RandomIterator2>& right);

template <class RandomIterator1, class RandomIterator2>
Tdiff operator-(
    const reverse_iterator<RandomIterator1>& left,
    const reverse_iterator<RandomIterator2>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
迭代器。

*right*<br/>
迭代器。

### <a name="return-value"></a>傳回值

兩個迭代器之間的差異`.`

### <a name="remarks"></a>備註

第一個範本運算子會傳回 `left.base() - right.base()`。

第二個範本運算子會傳回 `right.current - left.current`。

`Tdiff` 取決於所傳回運算式的類型。 否則為 `RandomIterator1::difference_type`。

### <a name="example"></a>範例

```cpp
// iterator_op_sub.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 0 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( ),
          rVPOS2 = vec.rbegin ( );

   cout << "The iterators rVPOS1 & rVPOS2 initially point to "
        << "the first element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   for (i = 1; i < 5; ++i)
   {
      rVPOS2++;
   }
   cout << "The iterator rVPOS2 now points to the fifth "
        << "element\n in the reversed sequence: "
        << *rVPOS2 << "." << endl;

   vector<int>::difference_type diff = rVPOS2 - rVPOS1;
   cout << "The difference: rVPOS2 - rVPOS1= "
        << diff << "." << endl;
}
```

```Output
The initial vector vec is: ( 0 2 4 6 8 10 ).
The iterators rVPOS1 & rVPOS2 initially point to the first element
in the reversed sequence: 10.
The iterator rVPOS2 now points to the fifth element
in the reversed sequence: 2.
The difference: rVPOS2 - rVPOS1= 4.
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>

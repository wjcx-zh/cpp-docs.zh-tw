---
title: reverse_iterator 類別
ms.date: 03/27/2019
f1_keywords:
- xutility/std::reverse_iterator
- iterator/std::reverse_iterator::difference_type
- iterator/std::reverse_iterator::iterator_type
- iterator/std::reverse_iterator::pointer
- iterator/std::reverse_iterator::reference
- iterator/std::reverse_iterator::base
- iterator/std::reverse_iterator::operator_star
helpviewer_keywords:
- std::reverse_iterator [C++]
- std::reverse_iterator [C++], difference_type
- std::reverse_iterator [C++], iterator_type
- std::reverse_iterator [C++], pointer
- std::reverse_iterator [C++], reference
- std::reverse_iterator [C++], base
- std::reverse_iterator [C++], operator_star
ms.assetid: c0b34d04-ae9a-4999-9aff-28b313897ffa
ms.openlocfilehash: 99fe323177c0aff29f5f01e6835bd800616e2e16
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889984"
---
# <a name="reverse_iterator-class"></a>reverse_iterator 類別

類別樣板是一個 iterator 介面卡，描述的反向反覆運算器物件的行為就像是隨機存取或雙向反覆運算器，只是反向。 它啟用範圍的向後周遊。

## <a name="syntax"></a>語法

```cpp
template <class RandomIterator>
class reverse_iterator
```

### <a name="parameters"></a>參數

RandomIterator 代表要調整以反向操作之反覆運算器的類型。

## <a name="remarks"></a>備註

現有的 C++ 標準程式庫容器也會定義 `reverse_iterator` 和 `const_reverse_iterator` 類型，並且具有可傳回反向迭代器的成員函式 `rbegin` 和 `rend`。 這些迭代器有覆寫語意。 `reverse_iterator` 介面卡會補充這種功能，因為它提供插入的語義，而且也可以與資料流程搭配使用。

需要雙向反覆運算器的 `reverse_iterator` 不得呼叫任何成員函式 `operator+=`、`operator+`、`operator-=`、`operator-`或 `operator[]`，這只能與隨機存取反覆運算器搭配使用。

反覆運算器的範圍是 [*first*， *last*），其中左邊的方括弧表示包含*第一個*，而右邊的括弧表示包含專案，但*最後一個*本身除外。 反向序列中會包含相同的元素 [ **rev** - *first*、 **rev** - *last*），因此，如果*last*是序列中的一個後端元素，則第一個專案的**rev** - 在反向序列中的第一個會指向 \*（*last* -1）。 將所有反向迭代器與其基礎迭代器關聯的識別為：

&\*（ **reverse_iterator** （ *i* ）） = = &\*（ *i* -1）。

實際上，這表示在反向序列中 reverse_iterator 會參考迭代器在原始序列中所參考項目之外 (右側) 一個位置的項目。 因此，如果迭代器定址序列 (2, 4, 6, 8) 中的項目 6，則 `reverse_iterator` 會定址反向序列 (8, 6, 4, 2) 中的項目 4。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[reverse_iterator](#reverse_iterator)|從基底迭代器建構預設的 `reverse_iterator` 或 `reverse_iterator`。|

### <a name="typedefs"></a>Typedef

|類型名稱|描述|
|-|-|
|[difference_type](#difference_type)|類型，提供兩個參考同一容器內項目的 `reverse_iterator` 之間的差異。|
|[iterator_type](#iterator_type)|類型，提供 `reverse_iterator` 的基礎迭代器。|
|[pointer](#pointer)|類型，提供指向 `reverse_iterator` 定址的項目之指標。|
|[reference](#reference)|類型，提供指向 `reverse_iterator` 定址的項目之參考。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[base](#base)|從其 `reverse_iterator` 復原基礎迭代器。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator_star](#op_star)|傳回 `reverse_iterator` 定址的項目。|
|[operator+](#op_add)|將位移新增至迭代器，並傳回新的 `reverse_iterator`，定址在新的位移位置中插入的項目。|
|[operator++](#op_add_add)|遞增 `reverse_iterator` 至下一個項目。|
|[operator+=](#op_add_eq)|加入 `reverse_iterator` 的指定位移。|
|[operator-](#operator-)|從 `reverse_iterator` 減去位移並傳回 `reverse_iterator`，定址在位移位置上的項目。|
|[operator--](#operator--)|遞減 `reverse_iterator` 至上一個項目。|
|[operator-=](#operator-_eq)|從 `reverse_iterator` 減去指定位移。|
|[operator->](#op-arrow)|傳回由 `reverse_iterator` 定址的項目之指標。|
|[operator&#91;&#93;](#op_at)|以指定的位置數目，從 `reverse_iterator` 定址的項目傳回項目位移的參考。|

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間:** std

## <a name="base"></a>  reverse_iterator::base

從其 `reverse_iterator` 復原基礎迭代器。

```cpp
RandomIterator base() const;
```

### <a name="return-value"></a>傳回值

構成 `reverse_iterator` 基礎的迭代器。

### <a name="remarks"></a>備註

將所有反向迭代器關聯至其基礎迭代器的識別為：

&\*（`reverse_iterator` （ *i* ）） = = &\*（ *i* -1）。

實際上，這表示在反向序列中，`reverse_iterator` 將參考迭代器在原始序列中所參考項目之外 (右側) 某個位置的項目。 因此，如果迭代器定址序列 (2, 4, 6, 8) 中的項目 6，則 `reverse_iterator` 會定址反向序列 (8, 6, 4, 2) 中的項目 4。

### <a name="example"></a>範例

```cpp
// reverse_iterator_base.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
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
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );
   cout << "The iterator pos points to: " << *pos << "." << endl;

   typedef reverse_iterator<vector<int>::iterator>::iterator_type it_vec_int_type;

   reverse_iterator<it_vec_int_type> rpos ( pos );
   cout << "The reverse_iterator rpos points to: " << *rpos
        << "." << endl;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
```

## <a name="difference_type"></a>  reverse_iterator::difference_type

類型，提供兩個參考同一容器內項目的 `reverse_iterator` 之間的差異。

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type  difference_type;
```

### <a name="remarks"></a>備註

`reverse_iterator` 差異類型與迭代器差異類型相同。

類型是迭代器特性 typename `iterator_traits`\< **RandomIterator**>  **::pointer** 的同義字。

### <a name="example"></a>範例

如需如何宣告及使用 `difference_type` 的範例，請參閱 [reverse_iterator::operator&#91;&#93;](#op_at)。

## <a name="iterator_type"></a>  reverse_iterator::iterator_type

類型，提供 `reverse_iterator` 的基礎迭代器。

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>備註

這個類型與樣板參數 `Iterator`同義。

### <a name="example"></a>範例

如需如何宣告及使用 `iterator_type` 的範例，請參閱 [reverse_iterator::base](#base)。

## <a name="op_star"></a>reverse_iterator：： operator\*

傳回 reverse_iterator 定址的項目。

```cpp
reference operator*() const;
```

### <a name="return-value"></a>傳回值

reverse_iterator 所定址的項目值。

### <a name="remarks"></a>備註

運算子會傳回 \* （**目前**-1）。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos, bpos;
   pos = find ( vec.begin ( ), vec.end ( ), 6 );

   // Declare a difference type for a parameter
   // declare a reference return type
   reverse_iterator<vector<int>::iterator>::reference refpos = *pos;
   cout << "The iterator pos points to: " << refpos << "." << endl;
}
```

## <a name="op_add"></a>  reverse_iterator::operator+

將位移新增至迭代器，並傳回新的 `reverse_iterator`，定址在新的位移位置中插入的項目。

```cpp
reverse_iterator<RandomIterator> operator+(difference_type Off) const;
```

### <a name="parameters"></a>參數

*關閉*\
要加入至反向迭代器的位移。

### <a name="return-value"></a>傳回值

為位移項目定址的 `reverse_iterator`。

### <a name="remarks"></a>備註

唯有在 `reverse_iterator` 滿足隨機存取迭代器的需求時，才能使用此成員函式。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_add.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 + 2; // offset added
   cout << "After the +2 offset, the iterator rVPOS2 points\n"
        << " to the 3rd element in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS2 points
to the 3rd element in the reversed sequence: 6.
```

## <a name="op_add_add"></a>  reverse_iterator::operator++

將 reverse_iterator 遞增至上一個項目。

```cpp
reverse_iterator<RandomIterator>& operator++();
reverse_iterator<RandomIterator> operator++(int);
```

### <a name="return-value"></a>傳回值

第一個運算子會傳回前置遞增的 `reverse_iterator`，而第二個後置遞增運算子會傳回遞增的 `reverse_iterator` 複本。

### <a name="remarks"></a>備註

唯有在 `reverse_iterator` 滿足雙向迭代器的需求時，才能使用此成員函式。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_incr.cpp
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
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1++;  // postincrement, preincrement: ++rVPSO1

   cout << "After incrementing, the iterator rVPOS1 points\n"
        << " to the second element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 9.
After incrementing, the iterator rVPOS1 points
to the second element in the reversed sequence: 7.
```

## <a name="op_add_eq"></a>  reverse_iterator::operator+=

加入 reverse_iterator 的指定位移。

```cpp
reverse_iterator<RandomIterator>& operator+=(difference_type Off);
```

### <a name="parameters"></a>參數

*關閉*\
要遞增迭代器的位移。

### <a name="return-value"></a>傳回值

由 `reverse_iterator` 定址之項目的參考。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_addoff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the last element
   vector <int>::reverse_iterator rVPOS1 = vec.rbegin ( );

   cout << "The iterator rVPOS1 initially points to the first "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1+=2;   // addition of an offset
   cout << "After the +2 offset, the iterator rVPOS1 now points\n"
        << " to the third element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator rVPOS1 initially points to the first element
in the reversed sequence: 10.
After the +2 offset, the iterator rVPOS1 now points
to the third element in the reversed sequence: 6.
```

## <a name="operator-"></a>  reverse_iterator::operator-

從 `reverse_iterator` 減去位移並傳回 `reverse_iterator`，定址在位移位置上的項目。

```cpp
reverse_iterator<RandomIterator> operator-(difference_type Off) const;
```

### <a name="parameters"></a>參數

*關閉*\
要從 reverse_iterator 中減去的位移。

### <a name="return-value"></a>傳回值

為位移項目定址的 `reverse_iterator`。

### <a name="remarks"></a>備註

唯有在 `reverse_iterator` 滿足隨機存取迭代器的需求時，才能使用此成員函式。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_sub.cpp
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
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   vector <int>::reverse_iterator rVPOS2 =rVPOS1 - 2; // offset subtracted
   cout << "After the -2 offset, the iterator rVPOS2 points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS2 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS2 points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="operator--"></a>  reverse_iterator::operator--

將 reverse_iterator 遞減至上一個項目。

```cpp
reverse_iterator<RandomIterator>& operator--();
reverse_iterator<RandomIterator> operator--(int);
```

### <a name="return-value"></a>傳回值

第一個運算子會傳回前置遞減的 `reverse_iterator`，而第二個後置遞減運算子會傳回遞減的 `reverse_iterator` 複本。

### <a name="remarks"></a>備註

唯有在 `reverse_iterator` 滿足雙向迭代器的需求時，才能使用此成員函式。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_decr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i - 1 );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;
   rVPOS1--;  // postdecrement, predecrement: --rVPSO1

   cout << "After the decrement, the iterator rVPOS1 points\n"
        << " to the next-to-last element in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 1 3 5 7 9 ).
The vector vec reversed is: ( 9 7 5 3 1 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 1.
After the decrement, the iterator rVPOS1 points
to the next-to-last element in the reversed sequence: 3.
```

## <a name="operator-_eq"></a>  reverse_iterator::operator-=

從 `reverse_iterator` 減去指定位移。

```cpp
reverse_iterator<RandomIterator>& operator-=(difference_type Off);
```

### <a name="parameters"></a>參數

*關閉*\
要從 `reverse_iterator` 中減去的位移。

### <a name="remarks"></a>備註

唯有在 `reverse_iterator` 滿足隨機存取迭代器的需求時，才能使用此成員函式。

運算子會評估**目前**的 + *關閉*，然後傳回 **\*此**。

### <a name="example"></a>範例

```cpp
// reverse_iterator_op_suboff.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 3 * i );
   }

   vector <int>::iterator vIter;

   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin( ) ; vIter != vec.end( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   // Initializing reverse_iterators to the first element
   vector <int>::reverse_iterator rVPOS1 = vec.rend ( ) - 1;

   cout << "The iterator rVPOS1 initially points to the last "
        << "element\n in the reversed sequence: "
        << *rVPOS1 << "." << endl;

   rVPOS1-=2;      // Subtraction of an offset
   cout << "After the -2 offset, the iterator rVPOS1 now points\n"
        << " to the 2nd element from the last in the reversed sequence: "
        << *rVPOS1 << "." << endl;
}
```

```Output
The vector vec is: ( 3 6 9 12 15 ).
The vector vec reversed is: ( 15 12 9 6 3 ).
The iterator rVPOS1 initially points to the last element
in the reversed sequence: 3.
After the -2 offset, the iterator rVPOS1 now points
to the 2nd element from the last in the reversed sequence: 9.
```

## <a name="op-arrow"></a>  reverse_iterator::operator-&gt;

傳回由 `reverse_iterator` 定址的項目之指標。

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>傳回值

由 `reverse_iterator` 定址之項目的指標。

### <a name="remarks"></a>備註

運算子會傳回 **&\*\*this**。

### <a name="example"></a>範例

```cpp
// reverse_iterator_ptrto.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back(pVector::value_type(1,2));
   vec.push_back(pVector::value_type(3,4));
   vec.push_back(pVector::value_type(5,6));

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::reverse_iterator rpvIter;
   cout << "The vector vec reversed is:\n( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++ )
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "The iterator pos points to:\n( " << pos -> first << ", "
   << pos -> second << " )" << endl << endl;

   pVector::reverse_iterator rpos (pos);

   // Use operator -> with return type: why type int and not int*
   int fint = rpos -> first;
   int sint = rpos -> second;

   cout << "The reverse_iterator rpos points to:\n( " << fint << ", "
   << sint << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The reverse_iterator rpos points to:
( 1, 2 )
```

## <a name="op_at"></a>  reverse_iterator::operator[]

以指定的位置數目，從 `reverse_iterator` 定址的項目傳回項目位移的參考。

```cpp
reference operator[](difference_type Off) const;
```

### <a name="parameters"></a>參數

*關閉*\
`reverse_iterator` 位址的位移。

### <a name="return-value"></a>傳回值

項目位移的參考。

### <a name="remarks"></a>備註

運算子會傳回 <strong>\*</strong>( **\*this** + `Off`)。

### <a name="example"></a>範例

```cpp
// reverse_iterator_ret_ref.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( 2 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 8 );
   reverse_iterator<vector<int>::iterator> rpos ( pos );

   // Declare a difference type for a parameter
   reverse_iterator<vector<int>::iterator>::difference_type diff = 2;

   cout << "The iterator pos points to: " << *pos << "." << endl;
   cout << "The iterator rpos points to: " << *rpos << "." << endl;

   // Declare a reference return type & use operator[]
   reverse_iterator<vector<int>::iterator>::reference refrpos = rpos [diff];
   cout << "The iterator rpos now points to: " << refrpos << "." << endl;
}
```

```Output
The vector vec is: ( 2 4 6 8 10 ).
The vector vec reversed is: ( 10 8 6 4 2 ).
The iterator pos points to: 8.
The iterator rpos points to: 6.
The iterator rpos now points to: 2.
```

## <a name="pointer"></a>  reverse_iterator::pointer

類型，提供指向 `reverse_iterator` 定址的項目之指標。

```cpp
typedef typename iterator_traits<RandomIterator>::pointer pointer;
```

### <a name="remarks"></a>備註

類型是迭代器特性 typename `iterator_traits`\< *RandomIterator*>  **::pointer** 的同義字。

### <a name="example"></a>範例

```cpp
// reverse_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

int main( )
{
   using namespace std;

   typedef vector<pair<int,int> > pVector;
   pVector vec;
   vec.push_back( pVector::value_type( 1,2 ) );
   vec.push_back( pVector::value_type( 3,4 ) );
   vec.push_back( pVector::value_type( 5,6 ) );

   pVector::iterator pvIter;
   cout << "The vector vec of integer pairs is:\n" << "( ";
   for ( pvIter = vec.begin ( ) ; pvIter != vec.end ( ); pvIter++)
      cout << "( " << pvIter -> first << ", " << pvIter -> second << ") ";
   cout << ")" << endl;

   pVector::reverse_iterator rpvIter;
   cout << "\nThe vector vec reversed is:\n" << "( ";
   for ( rpvIter = vec.rbegin( ) ; rpvIter != vec.rend( ); rpvIter++)
      cout << "( " << rpvIter -> first << ", " << rpvIter -> second << ") ";
   cout << ")" << endl;

   pVector::iterator pos = vec.begin ( );
   pos++;
   cout << "\nThe iterator pos points to:\n"
        << "( " << pos -> first << ", "
        << pos -> second << " )" << endl;

   pVector::reverse_iterator rpos (pos);
   cout << "\nThe iterator rpos points to:\n"
        << "( " << rpos -> first << ", "
        << rpos -> second << " )" << endl;
}
```

```Output
The vector vec of integer pairs is:
( ( 1, 2) ( 3, 4) ( 5, 6) )

The vector vec reversed is:
( ( 5, 6) ( 3, 4) ( 1, 2) )

The iterator pos points to:
( 3, 4 )

The iterator rpos points to:
( 1, 2 )
```

## <a name="reference"></a>  reverse_iterator::reference

類型，提供指向 reverse_iterator 定址之項目的參考。

```cpp
typedef typename iterator_traits<RandomIterator>::reference reference;
```

### <a name="remarks"></a>備註

類型是迭代器特性 typename `iterator_traits`\< *RandomIterator*>  **::reference** 的同義字。

### <a name="example"></a>範例

如需如何宣告和使用`reference`的範例，請參閱[reverse_iterator：： operator&#91; ](#op_at)或[reverse_iterator：： operator *](#op_star) 。

## <a name="reverse_iterator"></a>  reverse_iterator::reverse_iterator

從基底迭代器建構預設的 `reverse_iterator` 或 `reverse_iterator`。

```cpp
reverse_iterator();
explicit reverse_iterator(RandomIterator right);

template <class Type>
reverse_iterator(const reverse_iterator<Type>& right);
```

### <a name="parameters"></a>參數

*right* \
要調整為 `reverse_iterator` 的迭代器。

### <a name="return-value"></a>傳回值

調整基礎迭代器的預設 `reverse_iterator` 或 `reverse_iterator`。

### <a name="remarks"></a>備註

將所有反向迭代器與其基礎迭代器關聯的識別為：

&\*（`reverse_iterator` （ *i* ）） = = &\*（ *i* -1）。

實際上，這表示在反向序列中 reverse_iterator 會參考迭代器在原始序列中所參考項目之外 (右側) 一個位置的項目。 因此，如果迭代器定址序列 (2, 4, 6, 8) 中的項目 6，則 `reverse_iterator` 會定址反向序列 (8, 6, 4, 2) 中的項目 4。

### <a name="example"></a>範例

```cpp
// reverse_iterator_reverse_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 6 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   vector <int>::reverse_iterator rvIter;
   cout << "The vector vec reversed is: ( ";
   for ( rvIter = vec.rbegin( ) ; rvIter != vec.rend( ); rvIter++)
      cout << *rvIter << " ";
   cout << ")." << endl;

   vector <int>::iterator pos;
   pos = find ( vec.begin ( ), vec.end ( ), 4 );
   cout << "The iterator pos = " << *pos << "." << endl;

   vector <int>::reverse_iterator rpos ( pos );
   cout << "The reverse_iterator rpos = " << *rpos
        << "." << endl;
}
```

## <a name="see-also"></a>請參閱

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

---
title: '&lt;algorithm&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: c8c550be87eacf81fab994239e07ed2358fad39b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617656"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt; 函式

## <a name="adjacent_find"></a><a name="adjacent_find"></a>adjacent_find

搜尋等於或符合指定之條件的兩個相鄰項目。

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*pred*\
二元述詞提供所搜尋的範圍中相鄰元素的值要符合的條件。

### <a name="return-value"></a>傳回值

第一個相鄰專案的正向反覆運算器，彼此相等（在第一個版本中），或符合二元述詞所指定的條件（在第二個版本中），前提是找到這種類型的元素。 否則，會傳回指向*last*的反覆運算器。

### <a name="remarks"></a>備註

`adjacent_find` 演算法是非變化的序列演算法。 要搜尋的範圍必須有效；所有指標都必須可以取值，而且可透過遞增從第一個位置到達最後一個位置。 演算法的時間複雜性，在範圍內包含的元素數目中是線性。

`operator==` 用來決定元素間的比對，是否必須施加其運算元之間的對等關聯。

### <a name="example"></a>範例

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return elem1 * 2 == elem2;
}

int main()
{
    using namespace std;
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

    L.push_back( 50 );
    L.push_back( 40 );
    L.push_back( 10 );
    L.push_back( 20 );
    L.push_back( 20 );

    cout << "L = ( " ;
    for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
        cout << *Iter << " ";
    cout << ")" << endl;

    result1 = adjacent_find( L.begin( ), L.end( ) );
    if ( result1 == L.end( ) )
        cout << "There are not two adjacent elements that are equal."
            << endl;
    else
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a><a name="all_of"></a>all_of

當指定範圍內的每個專案都有條件時，傳回**true** 。

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示開始檢查條件的位置。 某範圍元素的開始迭代器標記。

*次*\
輸入迭代器，表示檢查條件的某範圍元素結尾。

*pred*\
要測試的條件。 這是使用者定義的述詞函式物件，可定義所檢查的元素所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

如果在指定範圍內的每個專案上偵測到條件，或如果範圍是空的，則傳回**true** ，否則傳回**false** 。

### <a name="remarks"></a>備註

只有在範圍中**true**的每個 `N` `[0, last - first)` `pred(*(first + N))` 都是**true**時，範本函數才會傳回 true。

### <a name="example"></a>範例

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a><a name="any_of"></a>any_of

當條件出現在指定的專案範圍中至少一次時，傳回**true** 。

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示檢查條件的某範圍元素開始。

*次*\
輸入迭代器，表示檢查條件的某範圍元素結尾。

*pred*\
要測試的條件。 這是由使用者定義的述詞函式物件所提供。 這個述詞定義所測試的元素所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

如果在指定的範圍內偵測到至少一次的條件，則傳回**true** ，如果從未偵測到條件，則傳回**false** 。

### <a name="remarks"></a>備註

只有在範圍內的某些中，範本函式才會傳回**true** `N`

範圍為 `[0, last - first)`，而情況是述詞 `pred(*(first + N))` 為 true。

### <a name="example"></a>範例

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a><a name="binary_search"></a>binary_search

測試已排序的範圍中是否有等於指定之值 (或在二元述詞指定的意義上，相當於該值) 的項目。

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*value*\
必要的值，比對元素值或必須符合條件的元素值與二元述詞所指定的元素值。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

如果在等於或等同于指定值的範圍中找到元素，則為**true** ;否則**為 false**。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在序列中，必須可透過遞增從第一個位置到達最後一個位置。

排序範圍必須根據 `binary_search` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

`binary_search`不會修改來源範圍。

正向迭代器的實值類型必須是小於比較才能建立此順序：因此若提供兩個元素，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元素之間的排序。

隨機存取反覆運算器的演算法複雜度是對數，否則為線性，另一種是以與（）成正比的步驟數目 `last`  -  `first` 。

### <a name="example"></a>範例

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list<int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a><a name="clamp"></a>夾具

比較值與上限和下限，並傳回值的參考（如果它介於界限之間），或如果值高於或低於其上方或下限，則傳回上限或下限的參考。

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>參數

*value*\
要與*upper*和*lower*比較的值。

*零下*\
要將*值*夾具的值下限。

*臨界*\
要將*值*夾具的值上限。

*pred*\
用來比較*值*與*lower*或*上限*的述詞。 比較述詞會採用兩個引數，如果第一個的意義小於第二個，則傳回**true** ，否則傳回**false**。

### <a name="return-value"></a>傳回值

傳回*較低*if 的參考 `value < lower` ，或傳回*大寫*if 的參考 `upper < value` 。 否則，它會傳回*值*的參考。

### <a name="remarks"></a>備註

如果*上限*小於*下限*，則行為是未定義的。

## <a name="copy"></a><a name="copy"></a>複製

從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以正向方向指派它們新位置。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，在來源範圍的第一個項目位置定址。

*次*\
輸入迭代器，用於定址來源範圍中最後一個項目的後面一個位置。

*destBeg*\
輸出迭代器，用於定址目的範圍中第一個項目的位置。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍中最後一個元素之後的位置，也就是反覆運算器定址 `result` + （*最後*  -  *一個*）。

### <a name="remarks"></a>備註

來源範圍必須是有效的，而且必須在目的端有足夠的空間保留所有項目的複本。

因為演算法從第一個元素開始依序複製來源元素，所以如果來源範圍的*最後一個*位置不包含在目的範圍中，則目的範圍可以與來源範圍重迭。 `copy`除非來源和目的範圍之間沒有重迭，否則可以用來將專案向左移，而不是向右移位。 若要向右移動任何數目的位置，請使用 [copy_backward](algorithm-functions.md#copy_backward) 演算法。

`copy` 演算法只修改迭代器指向的值，並指派新值給目的範圍的項目。 它不是用來建立新的項目，也不能直接將項目插入空的容器。

### <a name="example"></a>範例

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ii++ )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy the first 3 elements of v1 into the middle of v2
    copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the left
    copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a><a name="copy_backward"></a>copy_backward

從來源範圍將項目的值指定到目的範圍，逐一查看項目的來源序列，並以反向方向指派它們新位置。

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>參數

*頭*\
雙向迭代器，在來源範圍的第一個項目位置定址。

*次*\
雙向迭代器，在來源範圍中越過最後一個項目的位置定址。

*destEnd*\
雙向迭代器，在目的範圍中越過最後一個項目的位置定址。

### <a name="return-value"></a>傳回值

輸出反覆運算器，用於定址目的範圍中最後一個元素之後的位置，也就是說，反覆運算器會處理*destEnd* -（*最後*  -  *一個*）。

### <a name="remarks"></a>備註

來源範圍必須是有效的，而且必須在目的端有足夠的空間保留所有項目的複本。

`copy_backward`演算法會強加比演算法更嚴格的需求 `copy` 。 其輸入和輸出迭代器必須是雙向的。

`copy_backward` 和 [move_backward](algorithm-functions.md#move_backward) 演算法是指定輸出範圍並以迭代器指向目的範圍結尾的唯一 C++ 標準程式庫演算法。

因為演算法從最後一個元素開始依序複製來源元素，所以如果來源範圍的*第一個*位置不包含在目的範圍中，則目的範圍可以與來源範圍重迭。 除非來源和目的範圍之間沒有重疊，`copy_backward` 可以用來將項目向右位移，而不是向左移。 若要向左移動任何數目的位置，請使用 [copy](algorithm-functions.md#copy) 演算法。

`copy_backward` 演算法只修改迭代器指向的值，並指派新值給目的範圍的項目。 它不是用來建立新的項目，也不能直接將項目插入空的容器。

### <a name="example"></a>範例

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; ++i )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ++ii )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy_backward the first 3 elements of v1 into the middle of v2
    copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the right
    copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a><a name="copy_if"></a>copy_if

在某個範圍的專案中，針對指定的條件複製**true**的元素。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示檢查條件的範圍開始。

*次*\
輸入迭代器，表示範圍的結尾。

*dest*\
輸出迭代器，表示所複製元素的目的地。

*pred*\
測試範圍中每個元素的條件。 這種條件是由使用者定義的述詞函式物件所提供。 一元述詞會接受一個引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

針對每個符合條件的專案，等於*dest*的輸出反覆運算器會遞增一次。 換句話說，傳回值減去*dest*等於複製的元素數目。

### <a name="remarks"></a>備註

範本函式會針對下列項目評估一次：

`if (pred(*first + N)) * dest++ = *(first + N))`

範圍 `[0, last - first)` 中的每個 `N`，才能嚴格地從最低值開始增加 `N` 值。 如果*dest*和*第一次*指定儲存區，則*dest*不得在範圍內 `[ first, last )` 。

### <a name="example"></a>範例

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a><a name="copy_n"></a>copy_n

複製指定的項目數目。

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示要複製元素的位置。

*計數*\
帶正負號或不帶正負號的整數類型，指定要複製的元素數目。

*dest*\
輸出迭代器，表示要將元素複製過去的位置。

### <a name="return-value"></a>傳回值

傳回輸出迭代器，其中已將元素複製過去。 它與*dest*參數的傳回值相同。

### <a name="remarks"></a>備註

這個範本函式會針對範圍  中的每個  評估一次 `*(dest + N) = *(first + N))``N``[0, count)`，才能嚴格地從最低值開始增加 `N` 值。 然後它會傳回 `dest + N`。 如果*dest*和*第一次*指定儲存區，則*dest*不得在範圍內 `[first, last)` 。

### <a name="example"></a>範例

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a><a name="count"></a>計數

傳回範圍中值符合指定值的項目數目。

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，定址要周遊範圍中第一個元素的位置。

*次*\
輸入迭代器，定址要周遊範圍中最後一個元素之後的位置。

*value*\
要計算之元素的值。

### <a name="return-value"></a>傳回值

的差異類型 `InputIterator` ，計算具有值的範圍 [*first*， *last*）中的元素數目。 *value*

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

此演算法會進行一般化，以使用範本函式 [count_if](algorithm-functions.md#count_if) 來計算滿足任何述詞的元素。

### <a name="example"></a>範例

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a><a name="count_if"></a>count_if

傳回範圍中值符合指定條件的元素數。

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
輸入迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義計算元素時所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

符合此述詞所指定條件的元素數。

### <a name="remarks"></a>備註

這個範本函式是演算法 [count](algorithm-functions.md#count) 的概括，可以任意述詞取代述詞「等於特定值」。

### <a name="example"></a>範例

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a><a name="equal"></a>等於

逐一比較兩個範圍的每個項目是否相等 (或在二元述詞指定的意義上，是否對等)。

比較不同容器類型 (例如 `vector` 和 `list`) 中的元素時、比較不同的元素類型時，或需要比較容器的子範圍時，請使用 `std::equal`。 否則，在比較相同容器類型中相同類型的元素時，請使用提供給每個容器的非成員 `operator==`。

使用 C++14 程式碼中的雙重範圍多載，因為如果第二個範圍超過第一個範圍，只為第二個範圍採用單一迭代器的多載不會偵測到差異；而如果第二個範圍比第一個範圍短，則會導致未定義的行為。

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，定址要測試的第一個範圍中第一個項目的位置。

*last1*\
輸入迭代器，定址要測試的第一個範圍中最後一個項目的後面一個位置。

*first2*\
輸入迭代器，定址要測試的第二個範圍中第一個項目的位置。

*last2*\
輸入迭代器，定址要測試的第二個範圍中最後一個項目的後面一個位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

逐一比較元素時，只有在範圍在二元述詞下一致或相同時，才為 **true**，否則為 **false**。

### <a name="remarks"></a>備註

要搜尋的範圍必須有效；所有迭代器都必須可以取值，而且可透過遞增從第一個位置到達最後一個位置。

如果兩個範圍有相等的長度，則演算法的時間複雜性，在範圍包含的項目數目中是線性。 否則，函數會立即傳回**false**。

`operator==` 和使用者定義的述詞不需要在運算元之間強加對稱、自反和遞移的等價關係。

### <a name="example"></a>範例

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}
```

## <a name="equal_range"></a><a name="equal_range"></a>equal_range

如果提供排序範圍，則會尋找所有元素都等於指定值的子範圍。

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>參數

*頭*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*value*\
排序範圍中要搜尋的值。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="return-value"></a>傳回值

一對正向反覆運算器，指定包含在搜尋範圍內的子範圍，其中所有專案都等同于所使用之二元述詞所定義的意義（ *pred*或預設*值*，小於）。

如果範圍中沒有任何專案與*值*相等，則傳回的配對中的正向反覆運算器會相等，並指定可以插入*值*而不影響範圍順序的點。

### <a name="remarks"></a>備註

演算法所傳回配對的第一個迭代器是 [lower_bound](algorithm-functions.md#lower_bound)，而第二個迭代器是 [upper_bound](algorithm-functions.md#upper_bound)。

範圍必須根據提供給 `equal_range` 的述詞來進行排序。 例如，如果您要使用大於述詞，則必須以遞減順序排序範圍。

由傳回的反覆運算器配對所定義之可能空白子範圍中的元素， `equal_range` 將會相當於所使用之述詞所定義的意義中的*值*。

隨機存取反覆運算器的演算法複雜度是對數，否則為線性，另一種則是與（*最後*  -  *一個*）比例的步驟數目。

### <a name="example"></a>範例

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}
```

## <a name="fill"></a><a name="fill"></a>填滿

將相同的新值指派到指定範圍內的每個項目。

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，定址要周遊之範圍中第一個元素的位置。

*次*\
正向迭代器，定址要周遊之範圍中最後一個元素之後的位置。

*value*\
要指派給範圍 [*first*， *last*）中之元素的值。

### <a name="remarks"></a>備註

目的範圍必須有效；所有指標都必須可以取值，而且可透過遞增從第一個位置到達最後一個位置。 複雜度是具有範圍大小的線性。

### <a name="example"></a>範例

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Fill the last 5 positions with a value of 2
    fill( v1.begin( ) + 5, v1.end( ), 2 );

    cout << "Modified v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a><a name="fill_n"></a>fill_n

將新值指派給範圍中以特定元素開頭的指定元素數目。

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸出反覆運算器，用於定址要指派值*值*之範圍中第一個元素的位置。

*計數*\
帶正負號或不帶正負號的整數類型，指定要獲指派值的元素數目。

*value*\
要指派給範圍 [*first*， *first + count*）中之元素的值。

### <a name="return-value"></a>傳回值

專案的反覆運算器，如果*count* > 零，則緊接在最後一個元素之後，否則為第一個元素。

### <a name="remarks"></a>備註

目的範圍必須有效；所有指標都必須可以取值，而且可透過遞增從第一個位置到達最後一個位置。 複雜度是具有範圍大小的線性。

### <a name="example"></a>範例

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}
```

## <a name="find"></a><a name="find"></a>尋找

在範圍中找出有指定值的第一個項目的位置。

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，其定址要搜尋指定值的範圍中，第一個元素的位置。

*次*\
輸入迭代器，其定址要搜尋指定值的範圍中，最後一個元素後方的位置。

*value*\
要搜尋的值。

### <a name="return-value"></a>傳回值

輸入迭代器，其定址所搜尋的範圍中第一次出現的指定值。 如果找不到具有對等值的元素，則會傳回*last*。

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

如需使用 `find()` 的程式碼範例，請參閱 [find_if](algorithm-functions.md#find_if)。

## <a name="find_end"></a><a name="find_end"></a>find_end

在範圍中尋找與指定序列相同 (或在二元述詞指定的意義上，相當於該序列) 的最後一個子序列。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*first1*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*last1*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*first2*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*last2*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

正向反覆運算器，用於定址 [first1，last1）內最後一個子序列的第一個元素的位置，此專案符合指定的序列 [first2，last2）。

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。

### <a name="example"></a>範例

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for a match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent to those\n in v2 under the binary "
            << "predicate twice and that begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a><a name="find_first_of"></a>find_first_of

在目標範圍內搜尋第一次出現的任何多個值，或第一次出現的任何多個項目 (在二元述詞指定的意義上，相當於指定之項目集合)。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*first1*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*last1*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*first2*\
正向迭代器，其定址要比對範圍中第一個元素的位置。

*last2*\
正向迭代器，其定址要比對範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

正向迭代器會定址符合指定序列，或等於二元述詞所指定之意義的第一個子序列的第一個元素的位置。

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。

### <a name="example"></a>範例

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 3 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a><a name="find_if"></a>find_if

在範圍中找出滿足特定條件的第一個項目的位置。

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
輸入迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
輸入迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件或 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)，定義所搜尋的元素所要符合的條件。 一元述詞會接受單一引數，並在滿足時傳回**true** ，如果不符合，則傳回**false** 。 *Pred*的簽章必須有效地是 `bool pred(const T& arg);` ，其中 `T` 是可在取值 `InputIterator` 時以隱含方式轉換的類型。 **Const**關鍵字的顯示只是為了說明函式物件或 lambda 不應修改引數。

### <a name="return-value"></a>傳回值

輸入反覆運算器，參考範圍中符合述詞所指定之條件的第一個元素（述詞會產生**true**）。 如果找不到符合述詞的元素，則會傳回*last*。

### <a name="remarks"></a>備註

這個範本函式是演算法 [find](algorithm-functions.md#find) 的概括，可以任意述詞取代述詞「等於特定值」。 如邏輯相反 (尋找不符合述詞的第一個元素)，請參閱 [find_if_not](algorithm-functions.md#find_if_not)。

### <a name="example"></a>範例

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}
```

## <a name="find_if_not"></a><a name="find_if_not"></a>find_if_not

傳回指定範圍中不滿足條件的第一個項目。

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
輸入迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
輸入迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件或 [Lambda 運算式](../cpp/lambda-expressions-in-cpp.md)，定義所搜尋的元素不符合的條件。 一元述詞會接受單一引數，並在滿足時傳回**true** ，如果不符合，則傳回**false** 。 *Pred*的簽章必須有效地是 `bool pred(const T& arg);` ，其中 `T` 是可在取值 `InputIterator` 時以隱含方式轉換的類型。 **Const**關鍵字的顯示只是為了說明函式物件或 lambda 不應修改引數。

### <a name="return-value"></a>傳回值

輸入反覆運算器，參考範圍中不符合述詞所指定之條件的第一個元素（述詞會產生**false**）。 如果所有元素都符合述詞（述詞會針對每個元素產生**true** ），則會傳回*last*。

### <a name="remarks"></a>備註

這個範本函式是演算法 [find](algorithm-functions.md#find) 的概括，可以任意述詞取代述詞「等於特定值」。 如邏輯相反 (尋找不符合述詞的第一個元素)，請參閱 [find_if](algorithm-functions.md#find_if)。

如需快速適用於 `find_if_not()` 的程式碼範例，請參閱 [find_if](algorithm-functions.md#find_if)。

## <a name="for_each"></a><a name="for_each"></a>for_each

將指定的函式物件以正向順序套用至範圍內的每個項目，並傳回函式物件。

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>參數

*頭*\
輸入迭代器，定址要對其作業之範圍中第一個元素的位置。

*次*\
輸入迭代器，定址要對其作業之範圍中最後一個元素之後的位置。

*func*\
套用至範圍中每個元素的使用者定義函式物件。

### <a name="return-value"></a>傳回值

套用至範圍中的所有元素之後的函式物件複本。

### <a name="remarks"></a>備註

`for_each` 演算法極具彈性，可透過不同的使用者指定方式修改範圍內的每個元素。 傳遞不同的參數，即可透過修改後的形式重複使用範本化函式。 使用者定義的函式可能會累積內部狀態內的資訊，而演算法可能會在處理範圍中所有元素之後傳回這項資訊。

參考的範圍必須有效；所有指標必須是可取值且在序列中，還必須要可以從第一個位置開始透過增量而取得最後一個位置。

複雜度為線性，最多有（*最後*  -  *一次*）的比較。

### <a name="example"></a>範例

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) {
    }

    // The function call for the element to be multiplied
    void operator( ) ( Type& elem ) const
    {
        elem *= Factor;
    }
};

// The function object to determine the average
class Average
{
private:
    long num;      // The number of elements
    long sum;      // The sum of the elements
public:
    // Constructor initializes the value to multiply by
    Average( ) : num ( 0 ) , sum ( 0 )
    {
    }

    // The function call to process the next elment
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The local state of a function object can accumulate
    // information about a sequence of actions that the
    // return value can make available, here the Average
    double avemod2 = for_each ( v1.begin( ), v1.end( ),
        Average( ) );
    cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
            << avemod2 << "." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a><a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a><a name="generate"></a>創造

將函式物件產生的值指派給範圍內的每個項目。

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>參數

*頭*\
正向迭代器，定址要指派值之範圍中第一個元素的位置。

*次*\
正向迭代器，定址要指派值之範圍中最後一個元素之後的位置。

*代*\
不搭配引數呼叫的函式物件，用於產生要指派到範圍中每個項目的值。

### <a name="remarks"></a>備註

會為範圍中的每個項目叫用函式物件，且不需要在每次呼叫時傳回相同的值。 例如，其可能會從檔案讀取，或是參考及修改本機狀態。 產生器的結果類型必須是可以轉換為轉送至此範圍之迭代器的值類型。

參考的範圍必須有效；所有指標必須是可取值且在序列中，還必須要可以從第一個位置開始透過增量而取得最後一個位置。

複雜度為線性，需要有產生器的確切（ `last`  -  `first` ）呼叫。

### <a name="example"></a>範例

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
    using namespace std;

    // Assigning random values to vector integer elements
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

    generate ( v1.begin( ), v1.end( ), rand );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Assigning random values to deque integer elements
    generate ( deq1.begin( ), deq1.end( ), rand );

    cout << "Deque deq1 is ( " ;
    for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
        cout << *d1_Iter << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a><a name="generate_n"></a>generate_n

將函式物件產生的值指派給範圍內的指定項目數，並返回到超過最後一個指定值的位置。

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸出迭代器，指向範圍中第一個項目的位置 (要指派值至其中)。

*計數*\
帶正負號或不帶正負號的整數類型，指定要由產生器函式指派值的項目數。

*代*\
不搭配引數呼叫的函式物件，用於產生要指派到範圍中每個項目的值。

### <a name="remarks"></a>備註

會為範圍中的每個項目叫用函式物件，且不需要在每次呼叫時傳回相同的值。 例如，其可能會從檔案讀取，或是參考及修改本機狀態。 產生器的結果類型必須是可以轉換為轉送至此範圍之迭代器的值類型。

參考的範圍必須有效；所有指標必須是可取值且在序列中，還必須要可以從第一個位置開始透過增量而取得最後一個位置。

線性具有複雜度，因此需要對產生器執行明確的 `count` 呼叫。

### <a name="example"></a>範例

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}
```

## <a name="includes"></a><a name="includes"></a>包含

測試一個排序範圍是否包含第二個排序範圍內的所有項目，其中項目之間的順序或等價準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，定址要進行下列作業之兩個排序來源範圍的第一個範圍中第一個元素的位置：測試第二個範圍的所有元素是否都包含在第一個範圍中。

*last1*\
輸入迭代器，定址要進行下列作業之兩個排序來源範圍的第一個範圍中最後一個元素之後的位置：測試第二個範圍的所有元素是否都包含在第一個範圍中。

*first2*\
輸入迭代器，定址要進行下列作業之兩個連續排序來源範圍的第二個範圍中第一個元素的位置：測試第二個範圍的所有元素是否都包含在第一個範圍中。

*last2*\
輸入迭代器，定址要進行下列作業之兩個連續排序來源範圍的第二個範圍中最後一個元素之後的位置：測試第二個範圍的所有元素是否都包含在第一個範圍中。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="return-value"></a>傳回值

如果第一個排序範圍包含第二個排序範圍中的所有元素，則為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

考慮這項測試的另一種原因是它判斷第二個來源範圍是否為第一個來源範圍的子集。

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

每個排序來源範圍都必須根據 includes 演算法用來排序結合範圍的相同順序，排列成套用此演算法包含的前置條件。

演算法不會修改來源範圍 `merge` 。

輸入迭代器的實值類型必須小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 更精確地說，演算法會測試所指定二元述詞下第一個排序範圍中的所有元素是否都有第二個排序範圍中元素的對等順序。

此演算法的複雜度為線性，最多可 `2 * ((last1 - first1) - (last2 - first2)) - 1` 為非空白來源範圍進行比較。

### <a name="example"></a>範例

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
    bool Result1;
    Result1 = includes ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ) );
    if ( Result1 )
        cout << "All the elements in vector v1b are "
            << "contained in vector v1a." << endl;
    else
        cout << "At least one of the elements in vector v1b "
            << "is not contained in vector v1a." << endl;

    // To test for inclusion under descending
    // order specify binary predicate greater<int>( )
    bool Result2;
    Result2 = includes ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ), greater<int>( ) );
    if ( Result2 )
        cout << "All the elements in vector v2b are "
            << "contained in vector v2a." << endl;
    else
        cout << "At least one of the elements in vector v2b "
            << "is not contained in vector v2a." << endl;

    // To test for inclusion under a user
    // defined binary predicate mod_lesser
    bool Result3;
    Result3 = includes ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), mod_lesser );
    if ( Result3 )
        cout << "All the elements in vector v3b are "
            << "contained under mod_lesser in vector v3a."
            << endl;
    else
        cout << "At least one of the elements in vector v3b is "
            << " not contained under mod_lesser in vector v3a."
            << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a><a name="inplace_merge"></a>inplace_merge

將兩個連續排序範圍內的項目結合成單一排序範圍，其中順序準則可由二元述詞指定。

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，定址要結合並排序成單一範圍之兩個連續排序範圍的第一個範圍中第一個元素的位置。

*干預*\
雙向迭代器，定址要結合並排序成單一範圍之兩個連續排序範圍的第二個範圍中第一個元素的位置。

*次*\
雙向迭代器，定址要結合並排序成單一範圍之兩個連續排序範圍的第二個範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，而當第一個專案小於第二個元素時，應該傳回**true** ，否則傳回**false** 。

### <a name="remarks"></a>備註

參考的排序連續範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

每個排序連續範圍都必須根據 `inplace_merge` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。 因為會保留每個範圍內元素的相對順序，所以這項作業十分穩定。 兩個來源範圍中有對等元素時，結合範圍之第一個範圍中的元素會優先於第二個範圍中的元素。

因為演算法會將記憶體配置給暫存緩衝區，所以複雜度取決於可用記憶體。 如果有足夠的記憶體可用，最好的情況是具有 `(last - first) - 1` 比較的線性; 如果沒有輔助記憶體可用，則最壞的情況是 `N log(N)` ，其中*N*是  =  *最後*  -  *一個*。

### <a name="example"></a>範例

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
    break1 = find (v1.begin( ), v1.end( ), -5 );
    inplace_merge ( v1.begin( ), break1, v1.end( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Applying a user defined (UD) binary predicate mod_lesser
    inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a><a name="is_heap"></a>is_heap

如果指定範圍內的元素形成堆積，則傳回**true** 。

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
隨機存取迭代器，表示檢查堆積的範圍開始。

*次*\
隨機存取迭代器，表示範圍結尾。

*pred*\
要測試以排序元素的條件。 比較述詞會採用兩個引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

如果指定範圍中的元素形成堆積，則傳回**true** ，否則傳回**false** 。

### <a name="remarks"></a>備註

第一個範本函式會傳回[is_heap_until](algorithm-functions.md#is_heap_until) `(first , last) == last` 。

第二個範本函式會傳回

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a><a name="is_heap_until"></a>is_heap_until

傳回位於範圍 [，）中不符合堆積排序條件之第一個元素的反覆運算器 `first` `last` ; 如果範圍形成堆積，則為*結尾*。

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
隨機存取迭代器，指定要檢查有無堆積之範圍的第一個項目。

*次*\
隨機存取迭代器，指定要檢查有無堆積的範圍結尾。

*pred*\
二元述詞，指定定義堆積的嚴格弱式排序條件。 `std::less<>`當未指定*pred*時，預設的述詞為。

### <a name="return-value"></a>傳回值

如果指定的範圍形成堆積或包含一或多個元素，則傳回*last* 。 否則會傳回所找到第一個不符合堆積條件之項目的迭代器。

### <a name="remarks"></a>備註

第一個範本函式會傳回 `[first, last)` 中的最後一個迭代器 `next`，其中 `[first, next)` 是依函式物件 `std::less<>` 排序的堆積。 如果距離 `last - first` 小於2，函數會傳回*last*。

第二個範本函式的行為與第一個相同，不同之處在于它會使用述詞*pred* ，而不是 `std::less<>` 堆積排序條件。

## <a name="is_partitioned"></a><a name="is_partitioned"></a>is_partitioned

如果指定範圍中的條件測試**true**的所有專案都在測試**false**的任何專案之前，則傳回**true** 。

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示範圍開始檢查條件的位置。

*次*\
輸入迭代器，表示範圍結尾。

*pred*\
要測試的條件。 這是由使用者定義的述詞函式物件所提供，這個物件定義所搜尋的元素所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

當指定範圍中的所有專案在條件中測試**為 true**時，傳回**true** **，否則**傳回**false**。

### <a name="remarks"></a>備註

只有當中的所有專案都是由 pred 分割時，範本函式才會傳回**true** `[first, last)` ; 也就是說，中的所有專案都是 true，而所有專案*pred* `X` `[first, last)` `pred (X)` `Y` `pred (Y)` 都是**false**。

## <a name="is_permutation"></a><a name="is_permutation"></a>is_permutation

如果兩個範圍包含相同的項目，則不論項目的順序是否相同，都會傳回 true。 使用 C++14 程式碼中的雙重範圍多載，因為如果第二個範圍超過第一個範圍，只為第二個範圍採用單一迭代器的多載不會偵測到差異；而如果第二個範圍比第一個範圍短，則會導致未定義的行為。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*first1*\
指向範圍的第一個項目的正向迭代器。

*last1*\
指向範圍的最後項目前一個的正向迭代器。

*first2*\
指向第二個範圍的第一個項目的正向迭代器，用於比較。

*last2*\
指向第二個範圍的最後一個項目之某個項目的正向迭代器，用於比較。

*pred*\
述詞，用於測試是否相等並傳回**bool**。

### <a name="return-value"></a>傳回值

當範圍可以重新排列，使其根據比較子述詞而完全相同時，則為**true** ;否則**為 false**。

### <a name="remarks"></a>備註

`is_permutation` 在最壞的情況有二次方的複雜性。

第一個樣板函式假設範圍中的元素數目從*first2*開始，與指定的範圍相同 `[first1, last1)` 。 如果第二個範圍中有多個項目，就會忽略它們；如果更少，就會發生未定義的行為。 第三個樣板函式 (C++ 14 和更新版本) 不會進行這項假設。 只有在**true**指定範圍內的每個專案 x， `[first1, last1)` 其 x = = y 的相同範圍內有多個元素 Y 時，才會傳回 true，其範圍從*first2*或開始 `[first2, last2)` 。 在這裡， `operator==` 必須在其運算元之間執行成對比較。

第二個和第四個樣板函式的行為相同，不同之處是它們會以 `Pred(X, Y)` 取代 `operator==(X, Y)`。 若要正常運作，述詞必須對稱、自反和轉移。

### <a name="example"></a>範例

下列範例顯示如何使用 `is_permutation`：

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}
```

## <a name="is_sorted"></a><a name="is_sorted"></a>is_sorted

如果指定範圍內的專案為排序次序，則傳回**true** 。

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，表示要檢查之範圍的開始位置。

*次*\
正向迭代器，表示範圍結尾。

*pred*\
要測試以判斷兩個元素間之順序的條件。 比較述詞會採用兩個引數，並傳回**true**或**false**。 這會執行與 `operator<` 相同的工作。

### <a name="remarks"></a>備註

第一個範本函式會傳回[is_sorted_until](#is_sorted_until) `( first, last ) == last` 。 函式會 `operator<` 執行順序比較。

第二個範本函式會傳回 `is_sorted_until( first, last , pred ) == last`。 *Pred*述詞函式會執行順序比較。

## <a name="is_sorted_until"></a><a name="is_sorted_until"></a>is_sorted_until

傳回 `ForwardIterator`，以設定為指定範圍中依排序順序的最後一個元素。

第二個版本可讓您提供比較函式物件，以在兩個指定的專案為排序次序時傳回**true** ，否則為**false** 。

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，表示要檢查之範圍的開始位置。

*次*\
正向迭代器，表示範圍結尾。

*pred*\
要測試以判斷兩個元素間之順序的條件。 比較述詞會採用兩個引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

傳回設定為排序順序中最後一個元素的 `ForwardIterator`。 排序的序列會從*第一個*開始。

### <a name="remarks"></a>備註

第一個範本函式會傳回 `[first, last]` 中的最後一個迭代器 `next`，因此 `[first, next)` 是依 `operator<`所排列的排序序列。 如果 `distance()` 小於2，函數會傳回*last*。

第二個範本函式的行為相同，差異在於它會將 `operator<(X, Y)` 取代為 `pred(X, Y)`。

## <a name="iter_swap"></a><a name="iter_swap"></a>iter_swap

交換由一組指定之迭代器所參考的兩個值。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>參數

*左面*\
要交換其值的其中一個正向迭代器。

*再*\
要交換其值的第二個正向迭代器。

### <a name="remarks"></a>備註

`swap`應使用於**iter_swap**的喜好設定中，這是為了回溯相容性而包含在 c + + 標準中的。 如果 `Fit1` 和 `Fit2` 是正向反覆運算器，則 `iter_swap( Fit1, Fit2 )` 就相當於 `swap( *Fit1, *Fit2 )` 。

輸入正向迭代器的實值類型值必須相同。

### <a name="example"></a>範例

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) { m_nVal =
    rhs.m_nVal; return *this; }
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt(" << rhs.m_nVal << ")";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    CInt c1 = 5, c2 = 1, c3 = 10;
    deque<CInt> deq1;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Exchanging first and last elements with iter_swap
    iter_swap ( deq1.begin( ), --deq1.end( ) );

    cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping back first and last elements with swap
    swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

    cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping a vector element with a deque element
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        deq2.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque deq2 is ( " ;
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;

    iter_swap ( v1.begin( ), deq2.begin( ) );

    cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a><a name="lexicographical_compare"></a>lexicographical_compare

逐一比較兩個序列之間的每個項目，判斷兩者較小者。

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，定址要比較之第一個範圍中第一個元素的位置。

*last1*\
輸入迭代器，定址要比較之第一個範圍中最後一個元素之後的位置。

*first2*\
輸入迭代器，定址要比較之第二個範圍中第一個元素的位置。

*last2*\
輸入迭代器，定址要比較之第二個範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="return-value"></a>傳回值

如果第一個範圍由語彙方面上小於第二個範圍，則為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

序列間辭典編纂的比較會依元素逐一進行比較，直到符合下列其中一種情況：

- 發現兩個對應的元素不相等，並將其比較的結果作為序列間比較的結果。

- 找不到任何差異，但有一個序列的元素數比另一個序列還要多，因而將較短的序列視為小於較長的序列。

- 找不到任何到差異，而且序列具有相同數目的元素，因此序列相等，且比較結果為**false**。

### <a name="example"></a>範例

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    int ii;
    for ( ii = 0 ; ii <= 6 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Self lexicographical_comparison of v1 under identity
    bool result1;
    result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v1.begin( ), v1.end( ) );
    if ( result1 )
        cout << "Vector v1 is lexicographically_less than v1." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v1." << endl;

    // lexicographical_comparison of v1 and L2 under identity
    bool result2;
    result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                    L1.begin( ), L1.end( ) );
    if ( result2 )
        cout << "Vector v1 is lexicographically_less than L1." << endl;
    else
        cout << "Vector v1 is lexicographically_less than L1." << endl;

    bool result3;
    result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v2.begin( ), v2.end( ), twice );
    if ( result3 )
        cout << "Vector v1 is lexicographically_less than v2 "
            << "under twice." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v2 "
            << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a><a name="lower_bound"></a>lower_bound

在已排序範圍中尋找值大於或相當於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred );
```

### <a name="parameters"></a>參數

*頭*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*次*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*value*\
正在搜尋排序範圍中第一個位置或可能第一個位置的值。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

在已排序範圍中尋找值大於或相當於指定值的第一個元素的位置，其中順序準則可由二元述詞指定。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有迭代器都必須可以取值，而且在序列中，必須可透過遞增從第一個位置到達最後一個位置。

排序範圍是使用 `lower_bound` 的前置條件，而且順序與二元述詞所指定的順序相同。

`lower_bound`演算法不會修改範圍。

正向迭代器的實值類型必須小於比較才能建立此順序：因此若提供兩個元素，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元素之間的排序。

隨機存取反覆運算器的演算法複雜度是對數，否則為線性，另一種是以與（）成正比的步驟數目 `last - first` 。

### <a name="example"></a>範例

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a><a name="make_heap"></a>make_heap

將在指定範圍內的項目轉換為堆積，其中第一個項目是最大，而且排序準則可由二元述詞指定。

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred );
```

### <a name="parameters"></a>參數

*頭*\
隨機存取迭代器，定址要轉換為堆積之範圍中第一個元素的位置。

*次*\
隨機存取迭代器，定址要轉換為堆積之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="remarks"></a>備註

堆積有兩個屬性：

- 第一個元素一律最大。

- 可以在對數時間新增或移除元素。

堆積是實作優先順序佇列的理想方式，並且用於實作 C++ 標準程式庫容器配接器 [priority_queue 類別](priority-queue-class.md)。

複雜度為線性，需要進行 `3 * (last - first)` 比較。

### <a name="example"></a>範例

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="max"></a><a name="max"></a>讀數

比較兩個物件並傳回兩者較大者，其中順序準則可由二元述詞指定。

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*左面*\
正在比較的兩個物件之第一個。

*再*\
正在比較的兩個物件之第二個。

*pred*\
用來比較兩個物件的二元述詞。

*inlist*\
包含要比較的物件之初始設定式清單。

### <a name="return-value"></a>傳回值

兩個物件中較大的一個，除非兩者一樣大，在此情況下，它會傳回兩個物件的第一個。 在使用 initializer_list 的情況下，它會傳回此清單中最大的物件。

### <a name="remarks"></a>備註

`max` 是不尋常的演算法，因為它將物件做為參數傳遞。 大部分 C++ 標準程式庫演算法可對某範圍的元素作業，其位置由迭代器作為參數傳遞來加以指定。 如果您需要對某範圍元素運作的函式，請改用 [max_element](algorithm-functions.md#max_element)。 Visual Studio 2017 會在接受 initializer_list 的多載上啟用**constexpr** 。

### <a name="example"></a>範例

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = -elem1;
    if ( elem2 < 0 )
        elem2 = -elem2;
    return elem1 < elem2;
};

int main()
{
    int a = 6, b = -7;
    // Return the integer with the larger absolute value
    const int& result1 = max(a, b, abs_greater);
    // Return the larger integer
    const int& result2 = max(a, b);

    cout << "Using integers 6 and -7..." << endl;
    cout << "The integer with the greater absolute value is: "
            << result1 << "." << endl;
    cout << "The integer with the greater value is: "
            << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = max({ a, b });
    const int& result4 = max({ a, b }, abs_greater);

    cout << "Comparing the members of an initializer_list..." << endl;
    cout << "The member with the greater value is: " << result3 << endl;
    cout << "The integer with the greater absolute value is: " << result4 << endl;

    // Comparing set containers with elements of type CInt
    // using the max algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = max ( s1, s2 );
    cout << "s3 = max ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using the max algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = max ( v1, v2 );
    v5 = max ( v1, v3 );

    cout << "Vector v4 = max (v1,v2) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = max (v1,v3) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer with the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a><a name="max_element"></a>max_element

在指定的範圍內尋找第一個最大項目，其中順序準則可由二元述詞指定。

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，定址要搜尋最大元素之範圍中第一個元素的位置。

*次*\
正向迭代器，定址要搜尋最大元素之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，而當第一個專案小於第二個元素時，應該傳回**true** ，否則傳回**false** 。

### <a name="return-value"></a>傳回值

正向迭代器，定址所搜尋範圍中第一次出現最大元素的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度為線性： `(last - first) - 1` 非空白範圍需要進行比較。

### <a name="example"></a>範例

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the maximum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

    cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The largest element in v1 under the mod_lesser"
            << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a><a name="merge"></a>merge

將兩個排序來源範圍內的所有項目結合成單一排序目的範圍，其中順序準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，用於定址要結合並排序成單一範圍之兩個排序來源範圍的第一個範圍中，第一個項目的位置。

*last1*\
輸入迭代器，用於定址要結合並排序成單一範圍之兩個排序來源範圍的第一個範圍中，最後一個項目的後面一個位置。

*first2*\
輸入迭代器，用於定址要結合並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，第一個項目的位置。

*last2*\
輸入迭代器，用於定址要結合並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，最後一個項目的後面一個位置。

*result*\
輸出迭代器，用於定址目的範圍中第一個項目的位置，在此目的範圍中，兩個來源範圍會結合成單一排序範圍。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，而當第一個專案小於第二個元素時，應該傳回**true** ，否則傳回**false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址排序目的範圍中最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

目的範圍與任何一個來源範圍都不應該重疊，而且大小應該足以包含目的範圍。

每個排序來源範圍必須根據 `merge` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

這項作業很穩定，因為每個範圍內的項目相對順序會保留在目的範圍中。 演算法不會修改來源範圍 `merge` 。

輸入迭代器的實值類型必須小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 當兩個來源範圍中有對等元素時，目的範圍之第一個來源範圍中的元素會優先於第二個範圍中的元素。

演算法的複雜度為線性，最多有個 `(last1 - first1) - (last2 - first2) - 1` 比較。

[list 類別](list-class.md)提供成員函式 "merge" 來合併兩個清單的元素。

### <a name="example"></a>範例

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main() {
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a><a name="min"></a> 分鐘

比較兩個物件並傳回兩者較小者，其中順序準則可由二元述詞指定。

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);

template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*左面*\
正在比較的兩個物件之第一個。

*再*\
正在比較的兩個物件之第二個。

*pred*\
用來比較兩個物件的二元述詞。

*inlist*\
`initializer_list`，包含要比較的成員。

### <a name="return-value"></a>傳回值

除非兩者一樣大，否則會傳回兩個物件中較小的一個；在此情況下，它會傳回兩個物件的第一個。 如果是 `initializer_list` ，它會傳回清單中的最小物件。

### <a name="remarks"></a>備註

`min` 是不尋常的演算法，因為它將物件做為參數傳遞。 大部分 C++ 標準程式庫演算法可對某範圍的元素作業，其位置由迭代器作為參數傳遞來加以指定。 如果您需要使用某範圍元素的函式，請使用 [min_element](algorithm-functions.md#min_element)。 已在 Visual Studio 2017 中的多載上啟用[constexpr](../cpp/constexpr-cpp.md) `initializer_list` 。

### <a name="example"></a>範例

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
    // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a><a name="min_element"></a>min_element

在指定的範圍內尋找第一個最小項目，其中順序準則可由二元述詞指定。

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，定址要搜尋最小元素之範圍中第一個元素的位置。

*次*\
正向迭代器，定址要搜尋最小元素之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，而當第一個專案小於第二個元素時，應該傳回**true** ，否則傳回**false** 。

### <a name="return-value"></a>傳回值

正向迭代器，定址所搜尋範圍中第一次出現最小元素的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度為線性： `(last - first) - 1` 非空白範圍需要進行比較。

### <a name="example"></a>範例

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the minimum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

    cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a><a name="minmax_element"></a>minmax_element

在一個呼叫中執行 `min_element` 和 `max_element` 所執行的工作。

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，表示範圍開頭。

*次*\
正向迭代器，表示範圍結尾。

*pred*\
使用者定義的述詞函式物件，定義其中一個專案小於另一個元素的意義。 比較述詞會採用兩個引數，而且當第一個小於第二個時，應該傳回**true** ，否則傳回**false** 。

### <a name="return-value"></a>傳回值

傳回值

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>備註

第一個範本函式會傳回

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

第二個範本函式的行為相同，差異在於它會將 `operator<(X, Y)` 取代為 `pred(X, Y)`。

如果序列不是空的，此函式最多執行 `3 * (last - first - 1) / 2` 次比較。

## <a name="minmax"></a><a name="minmax"></a>minmax

比較兩個輸入參數並作為一組傳回，從小排到大。

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*左面*\
正在比較的兩個物件之第一個。

*再*\
正在比較的兩個物件之第二個。

*pred*\
用來比較兩個物件的二元述詞。

*inlist*\
`initializer_list`，包含要比較的成員。

### <a name="remarks"></a>備註

如果 right 小於 left，第一個範本函 `pair<const Type&, const Type&>( right, left )` *式*會傳回。 *right* 否則會傳回 `pair<const Type&, const Type&>( left, right )`。

第二個成員函式會傳回一個配對，其中第一個專案是較小的，而第二個則是比述詞*pred*更大的時間。

其餘範本函式的行為相同，不同之處在于它們會以*inlist*取代*left*和*right*參數。

此函式只會執行一個比較。

## <a name="mismatch"></a><a name="mismatch"></a>之

逐一比較兩個範圍的每個項目，找出差異發生的第一個位置。

使用 C++14 程式碼中的雙重範圍多載，因為如果第二個範圍超過第一個範圍，只為第二個範圍採用單一迭代器的多載不會偵測到差異；而如果第二個範圍比第一個範圍短，則會導致未定義的行為。

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，定址要測試的第一個範圍中第一個項目的位置。

*last1*\
輸入迭代器，定址要測試的第一個範圍中最後一個項目的後面一個位置。

*first2*\
輸入迭代器，定址要測試的第二個範圍中第一個項目的位置。

*last2*\
輸入迭代器，定址要測試的第二個範圍中最後一個項目的後面一個位置。

*pred*\
使用者定義述詞函式物件，比較每個範圍中的目前項目，並判斷是否相等。 符合時傳回 **true**，不符合則傳回 **false**。

### <a name="return-value"></a>傳回值

一組迭代器，定址兩個範圍中不相符的位置，第一個元件迭代器指向第一個範圍中的位置，而第二個元件迭代器指向第二個範圍中的位置。 如果比較的範圍中的項目之間沒有差異，或第二個版本中的二元述詞由兩個範圍的所有項目配對所滿足，則第一個元件迭代器會指向第一個範圍中最後一個項目的後面一個位置，而第二個元件迭代器會指向第二個範圍中測試的最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

第一個樣板函式會假設範圍中從 first2 開始的項目數，與 [first1, last1) 指定的範圍中的項目數相同。 如果第二個範圍中有更多，則會忽略它們;如果較少，則會產生未定義的行為。

要搜尋的範圍必須有效；所有迭代器都必須可以取值，而且可透過遞增從第一個位置到達最後一個位置。

在較短範圍內包含的項目數中，演算法的時間複雜性呈線性。

使用者定義的述詞不需要在運算元之間強加對稱、自反和遞移的等價關係。

### <a name="example"></a>範例

下列範例示範如何使用不相符。 顯示 C++03 多載只是為了示範可能產生非預期的結果。

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="ltalggt-move"></a><a name="alg_move"></a> &lt;alg&gt; move

移動與所指定範圍相關聯的項目。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示項目移動範圍的開始位置。

*次*\
輸入迭代器，表示項目移動範圍的結束位置。

*dest*\
要包含已移動項目的輸出迭代器。

### <a name="remarks"></a>備註

這個範本函式會針對範圍  中的每個  評估一次 `*(dest + N) = move(*(first + N))``N``[0, last - first)`，才能嚴格地從最低值開始增加 `N` 值。 然後它會傳回 `dest + N`。 如果 `dest` 和*第一次*指定儲存區，則*目的地*不得在範圍內 `[first, last)` 。

## <a name="move_backward"></a><a name="move_backward"></a>move_backward

將一個迭代器的項目移至另一個迭代器。 從指定範圍內的最後一個項目開始移動，並以該範圍內的第一個項目結束。

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>參數

*頭*\
迭代器，表示要從中移動元素的範圍開始。

*次*\
迭代器，表示要從中移動元素的範圍結尾。 這個元素不會進行移動。

*destEnd*\
雙向迭代器，在目的範圍中越過最後一個項目的位置定址。

### <a name="remarks"></a>備註

這個範本函式會針對範圍  中的每個  評估一次 `*(destEnd - N - 1) = move(*(last - N - 1))``N``[0, last - first)`，才能嚴格地從最低值開始增加 `N` 值。 然後它會傳回 `destEnd - (last - first)`。 如果*destEnd*和*第一次*指定儲存區， *destEnd*不得在範圍內 `[first, last)` 。

`move` 和 `move_backward` 的功能等同於搭配使用 `copy` 和 `copy_backward` 與移動迭代器。

## <a name="next_permutation"></a><a name="next_permutation"></a>next_permutation

重新排列範圍的項目，讓原始順序由語彙方面下一個較大的排列取代 (如果有的話)，其中下一個的意義可由二元述詞指定。

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
雙向迭代器，指向要排列之範圍中第一個元素的位置。

*次*\
雙向迭代器，指向要排列之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

如果由語彙方面下一個排列存在，並且已取代範圍的原始順序，則為 **true**；否則為 **false**，在這種情況下，順序會轉換為由語彙方面最小的排列。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

預設的二元述詞小於，而且範圍中的元素必須小於可比較的，以確保下一個排列已妥善定義。

複雜度為線性，最多可進行 `(last - first) / 2` 交換。

### <a name="example"></a>範例

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 5, c2 = 1, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically next permutation "
            << "exists and has\nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically next permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of next_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permuting vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a><a name="nth_element"></a>nth_element

分割某範圍的元素，將序列的第 *n* 個元素正確放入範圍中，以便在它前面的所有元素小於或等於它，而且序列中在它後面的所有元素大於或等於它。

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
隨機存取迭代器，定址要分割之範圍中第一個元素的位置。

*個*\
隨機存取迭代器，定址要在磁碟分割界限上正確排序之元素的位置。

*次*\
隨機存取迭代器，定址要分割之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

此 `nth_element` 演算法不保證會排序第*n*個元素的子範圍中的專案。 因此，它的保證低於 `partial_sort`，其可排序範圍中低於某個所選擇元素的元素，而且可以在不需要排序較低範圍時用作 `partial_sort` 的較快替代方式。

如果任一個都不小於另一個，則元素對等，但不一定相等。

排序複雜度的平均值是相對於*最後一個*的線性。

### <a name="example"></a>範例

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
    return elem1 > elem2;
}

int main() {
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 3 * i );

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
        v1.push_back( 3 * ii + 1 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 3 * iii +2 );

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
    cout << "Position 3 partitioned vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
            greater<int>( ) );
    cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    random_shuffle( v1.begin( ), v1.end( ) );
    cout << "Shuffled vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
    cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

## <a name="none_of"></a><a name="none_of"></a>none_of

當條件永遠不會出現在給定範圍中的專案之間時，傳回**true** 。

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示開始檢查條件之某範圍元素的位置。

*次*\
輸入迭代器，表示某範圍元素的結尾。

*pred*\
要測試的條件。 這是由定義該條件的使用者定義述詞函式物件所提供。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

如果在指定的範圍內至少偵測不到一次條件，則傳回**true** ，如果偵測到條件，則傳回**false** 。

### <a name="remarks"></a>備註

只有在範圍中的某些情況下，此範本函式才會傳回**true** `N` ，述詞 `[0, last - first)` 一律為 `pred(*(first + N))` **false**。

## <a name="partial_sort"></a><a name="partial_sort"></a>partial_sort

將範圍中指定的較小項目數目排列成非遞減排列，或是依據二元述詞指定的順序準則。

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。

*sortEnd*\
隨機存取迭代器，定址要排序之子範圍中最後一個元素之後的位置。

*次*\
隨機存取迭代器，定址要局部排序之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

如果任一個都不小於另一個，則元素對等，但不一定相等。 `sort`演算法不穩定，而且不保證會保留對等元素的相對順序。 `stable_sort` 演算法確實會保留這個原始順序。

平均部分排序複雜度為*O*（（ `last` -  `first` ） log （ `sortEnd` -  `first` ））。

### <a name="example"></a>範例

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii +1 );
    }

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
    cout << "Partially sorted vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To partially sort in descending order, specify binary predicate
    partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
    cout << "Partially resorted (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
    cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a><a name="partial_sort_copy"></a>partial_sort_copy

從來源範圍將項目複製到目的範圍，其中來源項目是依小於排序，或依據二元述詞指定的順序準則。

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，在來源範圍的第一個項目位置定址。

*last1*\
輸入迭代器，定址來源範圍中最後一個元素之後的位置。

*first2*\
隨機存取迭代器，定址排序目的範圍中第一個元素的位置。

*last2*\
隨機存取迭代器，定址排序目的範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

隨機存取迭代器，定址目的範圍中從來源範圍中插入之最後一個元素之後的元素的位置。

### <a name="remarks"></a>備註

來源與目的範圍不得重疊且必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

二元述詞必須提供嚴格弱式排序，因此會排序不對等的元素，但不會排序對等的元素。 如果任一個都不小於另一個，則兩個元素在進行小於運算下對等，但不一定相等。

### <a name="example"></a>範例

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a><a name="partition"></a>劃分

將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前。

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，定址要分割之範圍中第一個元素的位置。

*次*\
雙向迭代器，定址要分割之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義分類元素時所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

雙向迭代器，定址不符合述詞條件之範圍中第一個元素的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

如果*a*兩者都*b* `pred( a, b )` 是 false 且 `pred( b, a )` 為 false （其中*pred*是參數指定的述詞），元素 a 和 b 就相等，但不一定相等。 `partition`演算法不穩定，而且不保證會保留對等元素的相對順序。 `stable_partition` 演算法確實會保留這個原始順序。

複雜度為線性：有 pred 的 `(last - first)` 應用程式*pred*和最多的 `(last - first)/2` 交換。

### <a name="example"></a>範例

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }
    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    partition ( v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="partition_copy"></a><a name="partition_copy"></a>partition_copy

將條件為**true**的元素複製到一個目的地，並將其條件為**false** 。 項目必須來自指定的範圍。

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，表示檢查條件的範圍開始。

*次*\
輸入迭代器，表示範圍結尾。

*dest1*\
輸出反覆運算器，用來針對使用*pred*測試的條件，複製傳回 true 的元素。

*dest2*\
輸出反覆運算器，用來針對使用*pred*測試的條件，複製傳回 false 的元素。

*pred*\
要測試的條件。 這是由定義要測試之條件的使用者定義述詞函式物件所提供。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="remarks"></a>備註

如果為 true，則範本函式會將中的每個專案複製 `X` `[first,last)` 到 `*dest1++` `pred(X)` ，如果不是，則為 `*dest2++` 。 它會傳回 `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`。

## <a name="partition_point"></a><a name="partition_point"></a>partition_point

傳回給定範圍中不滿足條件的第一個項目。 排序項目，以便滿足條件的項目在不滿足條件的項目之前。

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
`ForwardIterator`，表示檢查條件的範圍開始。

*次*\
`ForwardIterator`，表示範圍結尾。

*pred*\
要測試的條件。 這是由使用者定義的述詞函式物件所提供，這個物件定義所搜尋的元素所要符合的條件。 一元述詞會接受單一引數，並傳回**true**或**false**。

### <a name="return-value"></a>傳回值

傳回，其參考不符合 `ForwardIterator` *pred*所測試之條件的第一個元素，或如果找不到，則傳回*最後*一個專案。

### <a name="remarks"></a>備註

此範本函式會尋找中的第一個反覆運算器為 `it` `[first, last)` `pred(*it)` **false**。 順序必須依*pred*排序。

## <a name="pop_heap"></a><a name="pop_heap"></a>pop_heap

從堆積的前面移動最大的項目至範圍的倒數第二個位置，然後從其餘項目形成新的堆積。

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
隨機存取迭代器，定址堆積中第一個元素的位置。

*次*\
隨機存取迭代器，定址堆積中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="remarks"></a>備註

`pop_heap` 演算法是 push_heap 演算法所執行作業的反向作業，其中，在範圍之倒數第二個位置的元素會新增至包含範圍中先前元素的堆積，前提是要新增至堆積的元素大於已在堆積中的任何元素時。

堆積有兩個屬性：

- 第一個元素一律最大。

- 可以在對數時間新增或移除元素。

堆積是實作優先順序佇列的理想方式，並且用於實作 C++ 標準程式庫容器配接器 [priority_queue 類別](priority-queue-class.md)。

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

結尾不包括新增元素的範圍必須是堆積。

複雜度為對數，最多需要 `log (last - first)` 比較。

### <a name="example"></a>範例

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    // Make v1 a heap with default less than ordering
    random_shuffle( v1.begin( ), v1.end( ) );
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the back of the heap
    v1.push_back( 10 );
    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove the largest element from the heap
    pop_heap( v1.begin( ), v1.end( ) );
    cout << "The heap v1 with 10 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater-than ordering with a 0 element
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    v1.push_back( 0 );
    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Application of pop_heap to remove the smallest element
    pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="prev_permutation"></a><a name="prev_permutation"></a>prev_permutation

重新排列範圍的元素，讓原始順序由語彙方面上一個較大的排列取代 (如果有的話)，其中上一個的意義可由二元述詞指定。

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
雙向迭代器，指向要排列之範圍中第一個元素的位置。

*次*\
雙向迭代器，指向要排列之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

如果詞典編纂上一個排列存在，並且已取代範圍的原始順序，**則為 true** ;否則**為 false**，在此情況下，會將順序轉換成詞典編纂最大的排列。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

預設的二元述詞小於，而且範圍中的元素必須小於比較，以確保先前的排列已妥善定義。

複雜度為線性，最多有（ `last`  -  `first` ）/2 次交換。

### <a name="example"></a>範例

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 1, c2 = 5, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically previous permutation "
            << "exists and has \nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically previous permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of prev_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permutating vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
        v1.push_back( i );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a><a name="push_heap"></a>push_heap

將在範圍結尾的項目加入至由範圍中之前項目所組成的現有堆積。

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*頭*\
隨機存取迭代器，定址堆積中第一個元素的位置。

*次*\
隨機存取迭代器，定址要轉換為堆積之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="remarks"></a>備註

元素必須先推送回現有堆積的結尾，接著會使用演算法將此元素新增至現有堆積。

堆積有兩個屬性：

- 第一個元素一律最大。

- 可以在對數時間新增或移除元素。

堆積是實作優先順序佇列的理想方式，並且用於實作 C++ 標準程式庫容器配接器 [priority_queue 類別](priority-queue-class.md)。

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

結尾不包括新增元素的範圍必須是堆積。

複雜度為對數，最多需要 `log(last - first)` 比較。

### <a name="example"></a>範例

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the heap
    v1.push_back( 10 );
    cout << "The heap v1 with 10 pushed back is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    v1.push_back(0);
    cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater than reheaped v1 with 11 added is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="random_shuffle"></a><a name="random_shuffle"></a>random_shuffle

Std：： random_shuffle （）函式已被取代，由[std：：隨機](algorithm-functions.md#shuffle)使用。 如需程式碼範例和詳細資訊，請參閱 [\<random>](random.md) 和 Stack Overflow 文章，[原因是 std：： random_shuffle 方法在 c + + 14 中被取代？](https://go.microsoft.com/fwlink/p/?linkid=397954)。

## <a name="remove"></a><a name="remove"></a>取消

從指定範圍中排除指定的值，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
轉送迭代器，定址要從中移除元素之範圍中，第一個元素的位置。

*次*\
轉送迭代器，定址要從中移除元素之範圍中，最後一個元素的位置後方。

*value*\
要從範圍中移除的值。

### <a name="return-value"></a>傳回值

轉送迭代器，定址修改過範圍的新結束位置，也就是指定值外的剩餘序列中，最後一個元素後方的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未移除之元素的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性;有 `last`  -  `first` 相等的（）比較。

[List 類別](list-class.md)具有更有效率的成員函式版本 `remove` ，這也會重新連結指標。

### <a name="example"></a>範例

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove ( v1.begin( ), v1.end( ), 7 );

    cout << "Vector v1 with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy"></a><a name="remove_copy"></a>remove_copy

從來源範圍將項目複製到目的範圍，不過不會複製一個指定值的項目，也不會干擾其餘項目的順序，並傳回新目的範圍結尾。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，用於定址要從中移除項目的範圍中，第一個項目的位置。

*次*\
輸入迭代器，用於定址要從中移除元素的範圍中，最後一個元素的後面一個位置。

*result*\
輸出迭代器，用於定址要移除元素的目的範圍中，第一個元素的位置。

*value*\
要從範圍中移除的值。

### <a name="return-value"></a>傳回值

正向迭代器，用於定址目的範圍的新結束位置，也就是指定值外的剩餘序列複本中，最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

參考的來源和目的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

目的範圍中的空間必須足以包含要在移除指定值的項目之後複製的剩餘項目。

未移除之元素的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性;有 `last`  -  `first` 相等的（）比較，而且最多有（ `last`  -  `first` ）個指派。

### <a name="example"></a>範例

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:     ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

    cout << "Vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a><a name="remove_copy_if"></a>remove_copy_if

將專案從來源範圍複製到目的範圍，但符合述詞的元素除外。 專案會複製，而不會干擾其餘元素的順序。 傳回新目的範圍的結尾。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，用於定址要從中移除項目的範圍中，第一個項目的位置。

*次*\
輸入迭代器，用於定址要從中移除元素的範圍中，最後一個元素的後面一個位置。

*result*\
輸出迭代器，用於定址要移除元素的目的範圍中，第一個元素的位置。

*pred*\
必須符合的一元述詞，也就是要被取代的項目值。

### <a name="return-value"></a>傳回值

正向迭代器，用於定址目的範圍的新結束位置，也就是符合述詞之元素外的剩餘序列中，最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

參考的來源範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

目的範圍中的空間必須足以包含要在移除指定值的項目之後複製的剩餘項目。

未移除之元素的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性：有 `last`  -  `first` 相等的（）比較，而且最多有（ `last`  -  `first` ）個指派。

如需這些函式運作方式的相關資訊，請參閱[已檢查的迭代器](checked-iterators.md)。

### <a name="example"></a>範例

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:      ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value greater than 6
    new_end = remove_copy_if ( v1.begin( ), v1.end( ),
        v2.begin( ), greater6 );

    cout << "After the appliation of remove_copy_if to v1,\n "
         << "vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with values greater "
         << "than 6 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_if"></a><a name="remove_if"></a>remove_if

從指定範圍中排除滿足述詞的項目，而不會干擾其餘項目的順序，並傳回沒有指定值、新範圍的結尾。

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，指向要從中移除元素之範圍中第一個元素的位置。

*次*\
正向迭代器，指向要從中移除元素之範圍中最後一個元素之後的位置。

*pred*\
必須符合的一元述詞，也就是要被取代的項目值。

### <a name="return-value"></a>傳回值

轉送迭代器，定址修改過範圍的新結束位置，也就是指定值外的剩餘序列中，最後一個元素後方的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未移除之元素的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性：有（ `last`  -  `first` ）比較是否相等。

list 具有更具效率之成員函式版本的 remove，而這會重新連結指標。

### <a name="example"></a>範例

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements satisfying predicate greater6
    new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

    cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace"></a><a name="replace"></a>取代

檢查範圍內的每個項目，如果符合指定的值則予以取代。

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，指向要從中取代元素之範圍中第一個元素的位置。

*次*\
正向迭代器，指向要從中取代元素之範圍中最後一個元素之後的位置。

*oldVal*\
所取代之項目的舊值。

*newVal*\
要指派給具有舊值之項目的新值。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未取代之項目的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性;有相等的（ `last`  -  `first` ）比較，而且最多有（ `last`  -  `first` ）個新值指派。

### <a name="example"></a>範例

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 with a value of 700
    replace (v1.begin( ), v1.end( ), 7 , 700);

    cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy"></a><a name="replace_copy"></a>replace_copy

檢查來源範圍內的每個項目，如果符合指定的值則予以取代，同時將結果複製到新目的範圍。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，用於指向要從中取代項目的範圍中，第一個項目的位置。

*次*\
輸入迭代器，用於指向要從中取代項目的範圍中，最後一個項目的後面一個位置。

*result*\
輸出迭代器，用於指向要複製已更改順序的項目之目的範圍中，第一個項目的位置。

*oldVal*\
所取代之項目的舊值。

*newVal*\
要指派給具有舊值之項目的新值。

### <a name="return-value"></a>傳回值

輸出反覆運算器，指向目的範圍中最後一個元素的後面一個位置，這是複製的元素順序。

### <a name="remarks"></a>備註

參考的來源和目的範圍不得重疊且必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未取代之項目的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性：有相等的（ `last`  -  `first` ）比較，而且最多有（ `last`  -  `first` ）個新值指派。

### <a name="example"></a>範例

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 15 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in one part of a vector with a value of 7
    // with a value of 70 and copy into another part of the vector
    replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

    cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

    cout << "The list copy L1 of v1 with the value 0 replacing "
            << "that of 7 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a><a name="replace_copy_if"></a>replace_copy_if

檢查來源範圍內的每個項目，如果滿足指定的述詞則予以取代，同時將結果複製到新目的範圍。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
輸入迭代器，用於指向要從中取代項目的範圍中，第一個項目的位置。

*次*\
輸入迭代器，用於指向要從中取代項目的範圍中，最後一個項目的後面一個位置。

*result*\
輸出迭代器，用於指向要複製元素之目的範圍中，第一個元素的位置。

*pred*\
必須符合的一元述詞，也就是要被取代的項目值。

*value*\
要指派給其舊值符合此述詞之項目的新值。

### <a name="return-value"></a>傳回值

輸出反覆運算器，指向目的範圍中最後一個元素的後面一個位置，這是複製的元素順序。

### <a name="remarks"></a>備註

參考的來源和目的範圍不得重疊且必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未取代之項目的順序會保持穩定。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性;有相等的（ `last`  -  `first` ）比較，而且最多有（ `last`  -  `first` ）個新值指派。

### <a name="example"></a>範例

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 13 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 in the 1st half of a vector
    // with a value of 70 and copy it into the 2nd half of the vector
    replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
        greater6 , 70);

    cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
        greater6 , -1 );

    cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_if"></a><a name="replace_if"></a>replace_if

檢查範圍內的每個項目，如果滿足指定的述詞則予以取代。

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，指向要從中取代元素之範圍中第一個元素的位置。

*次*\
迭代器，指向要從中取代元素之範圍中最後一個元素之後的位置。

*pred*\
必須符合的一元述詞，也就是要被取代的項目值。

*value*\
要指派給其舊值符合此述詞之項目的新值。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

未取代之項目的順序會保持穩定。

演算法 `replace_if` 是演算法的一般化 `replace` ，允許指定任何述詞，而不是等於指定的常數值。

用來判斷元素是否相等的 `operator==` 必須在其運算元之間具有對等關聯。

複雜度為線性：有相等的（ `last`  -  `first` ）比較，而且最多有（ `last`  -  `first` ）個新值指派。

### <a name="example"></a>範例

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements satisfying the predicate greater6
    // with a value of 70
    replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

    cout << "The vector v1 with a value 70 replacing those\n "
         << "elements satisfying the greater6 predicate is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="reverse"></a><a name="reverse"></a>反向

反轉範圍內項目的順序。

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，指向要排列元素之範圍中第一個元素的位置。

*次*\
雙向迭代器，指向要排列元素之範圍中最後一個元素之後的位置。

### <a name="remarks"></a>備註

參考的來源範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

### <a name="example"></a>範例

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse (v1.begin( ), v1.end( ) );

    cout << "The modified vector v1 with values reversed is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a><a name="reverse_copy"></a>reverse_copy

反轉來源範圍內項目的順序，並將其複製到目的範圍

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，用於指向要排列的來源範圍中，第一個元素的位置。

*次*\
雙向迭代器，用於指向要排列元素的來源範圍中，最後一個元素的後面一個位置。

*result*\
輸出迭代器，用於指向要複製元素之目的範圍中，第一個元素的位置。

### <a name="return-value"></a>傳回值

輸出反覆運算器，指向目的範圍中最後一個元素的後面一個位置，這是複製的元素順序。

### <a name="remarks"></a>備註

參考的來源和目的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

### <a name="example"></a>範例

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

    cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "The original vector v1 remains unmodified as:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="rotate"></a><a name="rotate"></a>向

交換兩個相鄰範圍的項目。

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，用於定址要旋轉之範圍中第一個項目的位置。

*干預*\
定義範圍內界限的正向迭代器，用於定址第二個範圍部分中第一個項目的位置，該部分的項目會與第一個範圍部分的項目交換。

*次*\
正向迭代器，用於定址要旋轉之範圍中最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度為線性，最多有（ `last`  -  `first` ）次交換。

### <a name="example"></a>範例

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
    {
        d1.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a><a name="rotate_copy"></a>rotate_copy

交換來源範圍內兩個相鄰範圍的項目，並將結果複製到目的範圍。

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，用於定址要旋轉之範圍中第一個項目的位置。

*干預*\
定義範圍內界限的正向迭代器，用於定址第二個範圍部分中第一個項目的位置，該部分的項目會與第一個範圍部分的項目交換。

*次*\
正向迭代器，用於定址要旋轉之範圍中最後一個項目的後面一個位置。

*result*\
輸出迭代器，用於定址目的範圍中第一個項目的位置。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址目的範圍中最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度為線性，最多有（ `last`  -  `first` ）次交換。

### <a name="example"></a>範例

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a><a name="sample"></a>抽樣

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a><a name="search"></a>search

在目標範圍中搜尋第一個序列，其項目等於指定項目序列中的項目，或在二元述詞指定的意義上，其項目相當於指定序列中的項目。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*last1*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*first2*\
正向迭代器，其定址要比對範圍中第一個元素的位置。

*last2*\
正向迭代器，其定址要比對範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

*搜索*\
封裝要尋找之模式的搜尋，以及要使用的搜尋演算法。 如需 searchers 的詳細資訊，請參閱[default_searcher 類別](default-searcher-class.md)、 [boyer_moore_horspool_searcher 類別](boyer-moore-horspool-searcher-class.md)和[boyer_moore_searcher 類別](boyer-moore-searcher-class.md)。

### <a name="return-value"></a>傳回值

正向迭代器會定址符合指定序列，或等於二元述詞所指定之意義的第一個子序列的第一個元素的位置。

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。

平均複雜性是與所搜尋範圍大小有關的線性，而最差狀況複雜性也是與所搜尋序列大小有關的線性。

### <a name="example"></a>範例

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a><a name="search_n"></a>search_n

在範圍中搜尋包含指定項目數的第一個子序列，這些項目具有特定值或在二元述詞指定的意義上與該值關聯。

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
正向迭代器，其定址要搜尋範圍中第一個元素的位置。

*last1*\
正向迭代器，其定址要搜尋範圍中最後一個元素之後的位置。

*計數*\
所搜尋子序列的大小。

*value*\
所搜尋序列中元素的值。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

正向迭代器會定址符合指定序列，或等於二元述詞所指定之意義的第一個子序列的第一個元素的位置。

### <a name="remarks"></a>備註

`operator==` 用來決定元素及指定值間的比對，是否必須施加其運算元之間的等價關聯。

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度是與所搜尋範圍大小有關的線性。

### <a name="example"></a>範例

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
    return elem1 == 2 * elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
    result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

    if ( result2 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1"
            << " under the equivalence predicate one_half." << endl;
    else
        cout << "There is a match of a sequence ( 5 5 5 ) "
            << "under the equivalence\n predicate one_half "
            << "in v1 and the first one begins at "
            << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a><a name="set_difference"></a>set_difference

將屬於一個排序來源範圍但不屬於第二個排序來源範圍的所有項目聯集為單一排序的目的範圍，其中順序準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的差異。

*last1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的差異。

*first2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的差異。

*last2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的差異。

*result*\
輸出迭代器，用於定址目的範圍中第一個元素的位置，在此目的範圍中，兩個來源範圍會聯集成單一排序範圍，以代表兩個來源範圍的差異。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 此二元述詞接受兩個引數，若第一個元素小於第二個元素，即傳回 **true** ；否則傳回 **false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址排序目的範圍中最後一個元素的後面一個位置，此目的範圍代表兩個來源範圍的差異。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

目的範圍與任何一個來源範圍都不應該重疊，而且大小應該足以包含第一個來源範圍。

每個排序來源範圍必須根據 `set_difference` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

這項作業很穩定，因為每個範圍內的項目相對順序會保留在目的範圍中。 演算法 merge 不會修改來源範圍。

輸入迭代器的實值類型必須是小於比較才能建立此順序：因此若提供了兩個元素，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 當兩個來源範圍中有對等元素時，目的範圍之第一個來源範圍中的元素會優先於第二個範圍中的元素。 如果來源範圍包含重複的元素，使得第一個來源範圍中的元素比第二個來源範圍多，則目的範圍會包含第一個來源範圍中這些元素的發生次數超過第二個來源範圍中這些元素的發生次數的數目。

此演算法的複雜度為線性，最多可 `2 * ((last1 - first1) - (last2 - first2)) - 1` 為非空白來源範圍進行比較。

### <a name="example"></a>範例

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a><a name="set_intersection"></a>set_intersection

將屬於兩個排序來源範圍的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的交集。

*last1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的交集。

*first2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的交集。

*last2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的交集。

*result*\
輸出迭代器，用於定址目的範圍中第一個元素的位置，在此目的範圍中，兩個來源範圍會聯集成單一排序範圍，以代表兩個來源範圍的交集。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 此二元述詞接受兩個引數，若第一個元素小於第二個元素，即傳回 **true** ；否則傳回 **false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址排序目的範圍中最後一個元素的後面一個位置，此目的範圍代表兩個來源範圍的交集。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

目的範圍與任何一個來源範圍都不應該重疊，而且大小應該足以包含目的範圍。

每個排序來源範圍必須根據 merge 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

這項作業很穩定，因為每個範圍內的項目相對順序會保留在目的範圍中。 演算法不會修改來源範圍。

輸入迭代器的實值類型必須小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 當兩個來源範圍中有對等元素時，目的範圍之第一個來源範圍中的元素會優先於第二個範圍中的元素。 如果來源範圍包含重複的元素，則目的範圍會包含這些元素同時出現在兩個來源範圍中的最大數量元素。

此演算法的複雜度為線性，最多可 `2 * ((last1 - first1) + (last2 - first2)) - 1` 為非空白來源範圍進行比較。

### <a name="example"></a>範例

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a><a name="set_symmetric_difference"></a>set_symmetric_difference

將屬於兩個排序來源範圍之一 (但非兩者) 的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，第一個項目的位置，此聯集範圍代表兩個來源範圍的對稱差。

*last1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，最後一個項目的後面一個位置，此聯集範圍代表兩個來源範圍的對稱差。

*first2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，第一個項目的位置，此聯集範圍代表兩個來源範圍的對稱差。

*last2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，最後一個項目的後面一個位置，此聯集範圍代表兩個來源範圍的對稱差。

*result*\
輸出迭代器，用於定址目的範圍中第一個項目的位置，在此目的範圍中，兩個來源範圍會聯集成單一排序範圍，以代表兩個來源範圍的對稱差。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 此二元述詞接受兩個引數，若第一個元素小於第二個元素，即傳回 **true** ；否則傳回 **false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址排序目的範圍中最後一個項目的後面一個位置，此目的範圍代表兩個來源範圍的對稱差。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

目的範圍與任何一個來源範圍都不應該重疊，而且大小應該足以包含目的範圍。

每個排序來源範圍必須根據 `merge*` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

這項作業很穩定，因為每個範圍內的項目相對順序會保留在目的範圍中。 演算法 merge 不會修改來源範圍。

輸入迭代器的實值類型必須小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 當兩個來源範圍中有對等元素時，目的範圍之第一個來源範圍中的元素會優先於第二個範圍中的元素。 如果來源範圍包含重複的項目，且這些項目在其中一個來源範圍中出現的數目，超過在第二個來源範圍中出現的數目，則目的範圍會包含同時出現之數目的絕對值。

此演算法的複雜度為線性，最多可 `2 * ((last1 - first1) - (last2 - first2)) - 1` 為非空白來源範圍進行比較。

### <a name="example"></a>範例

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a><a name="set_union"></a>set_union

將至少屬於兩個排序來源範圍之一的所有項目聯集為單一排序目的範圍，其中順序準則可由二元述詞指定。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的聯集。

*last1*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個排序來源範圍的第一個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的聯集。

*first2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，第一個元素的位置，此聯集範圍代表兩個來源範圍的聯集。

*last2*\
輸入迭代器，用於定址要聯集並排序成單一範圍之兩個連續排序來源範圍的第二個範圍中，最後一個元素的後面一個位置，此聯集範圍代表兩個來源範圍的聯集。

*result*\
輸出迭代器，用於定址目的範圍中第一個元素的位置，在此目的範圍中，兩個來源範圍會聯集成單一排序範圍，以代表兩個來源範圍的聯集。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 此二元述詞接受兩個引數，若第一個元素小於第二個元素，即傳回 **true** ；否則傳回 **false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址排序目的範圍中最後一個元素的後面一個位置，此目的範圍代表兩個來源範圍的聯集。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。

目的範圍與任何一個來源範圍都不應該重疊，而且大小應該足以包含目的範圍。

每個排序來源範圍必須根據 `merge` 演算法用來排序結合範圍的相同順序，排列成套用此演算法的前置條件。

這項作業很穩定，因為每個範圍內的項目相對順序會保留在目的範圍中。 演算法不會修改來源範圍 `merge` 。

輸入迭代器的實值類型必須小於比較才能建立此順序：因此若提供了兩個項目，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元件之間的排序。 當兩個來源範圍中有對等元素時，目的範圍之第一個來源範圍中的元素會優先於第二個範圍中的元素。 如果來源範圍包含重複的元素，則目的範圍會包含這些元素同時出現在兩個來源範圍中的最大數量元素。

演算法的複雜度為線性，最多有個 `2 * ((last1 - first1) - (last2 - first2)) - 1` 比較。

### <a name="example"></a>範例

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a><a name="shuffle"></a>播放

使用亂數產生器隨機播放 (重新整理) 指定範圍的元素。

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>參數

*頭*\
範圍中要隨機播放之第一個元素的迭代器，內含。 必須符合 `RandomAccessIterator` 和 `ValueSwappable` 的需求。

*次*\
範圍中要隨機播放之最後一個元素的迭代器，專用。 必須符合 `RandomAccessIterator` 和 `ValueSwappable` 的需求。

*代*\
`shuffle()` 函式將用於作業的亂數產生器。 必須符合 `UniformRandomNumberGenerator` 的需求。

### <a name="remarks"></a>備註

如需詳細資訊以及使用的程式碼範例， `shuffle()` 請參閱 [\<random>](random.md) 。

## <a name="sort"></a><a name="sort"></a>方式

將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則。

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
隨機存取迭代器，用於定址要排序之範圍中第一個項目的位置。

*次*\
隨機存取迭代器，用於定址要排序之範圍中越過最後一個項目的第一個位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 此二元述詞接受兩個引數，並在兩個引數為順序時傳回**true** ，否則傳回**false** 。 這個比較子函式必須對序列中項目的配對強制執行嚴格的弱式順序。 如需詳細資訊，請參閱[演算法](algorithms.md)。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

如果任一個都不小於另一個，則元素對等，但不一定相等。 `sort` 演算法不穩定，因此不保證保留對等元素的相對順序。 `stable_sort` 演算法確實會保留這個原始順序。

排序複雜度的平均值是 `O( N log N )` ，其中 N 是*N*  =  *最後*  -  *一個*。

### <a name="example"></a>範例

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii + 1 );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    sort( v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order. specify binary predicate
    sort( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    sort( v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a><a name="sort_heap"></a>sort_heap

將堆積轉換為排序的範圍。

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*頭*\
隨機存取迭代器，定址目標堆積中第一個元素的位置。

*次*\
隨機存取迭代器，定址目標堆積中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義一個元素小於另一個元素的意義。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="remarks"></a>備註

堆積有兩個屬性：

- 第一個元素一律最大。

- 可以在對數時間新增或移除元素。

套用此演算法之後，所套用的範圍就不再是堆積。

因為不一定保留對等元素的相對順序，所以這不是穩定的排序。

堆積是實作優先順序佇列的理想方式，並且用於實作 C++ 標準程式庫容器配接器 [priority_queue 類別](priority-queue-class.md)。

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

複雜程度最高 `N log N` ，其中*N*是  =  *最後*  -  *一次*。

### <a name="example"></a>範例

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a><a name="stable_partition"></a>stable_partition

將範圍中的項目分類為兩個斷續集合，而滿足一元述詞的項目在無法滿足一元述詞的項目之前，保留對等項目的相對順序。

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，定址要分割之範圍中第一個元素的位置。

*次*\
雙向迭代器，定址要分割之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義分類元素時所要符合的條件。 一元述詞會接受單一引數，並在滿足時傳回**true** ，如果不符合，則傳回**false** 。

### <a name="return-value"></a>傳回值

雙向迭代器，定址不符合述詞條件之範圍中第一個元素的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

如果*a*兩者都*b* `pred( a, b )` 是 false 且 `pred( b, a )` 為 false （其中*pred*是參數指定的述詞），元素 a 和 b 就相等，但不一定相等。 `stable_partition`演算法是穩定的，可保證會保留對等元素的相對順序。 演算法 `partition` 不一定會保留這種原始順序。

### <a name="example"></a>範例

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 4 ; ii++ )
        v1.push_back( 5 );

    random_shuffle(v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    result = stable_partition (v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "The first element in v1 to fail to satisfy the"
         << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a><a name="stable_sort"></a>stable_sort

將在指定範圍中的項目排列成非遞減排列，或是依據二元述詞指定的順序準則，並保留對等項目的相對順序。

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
雙向迭代器，定址要排序之範圍中第一個元素的位置。

*次*\
雙向迭代器，定址要排序之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義順序中後續元素所要符合的比較準則。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。

如果任一個都不小於另一個，則元素對等，但不一定相等。 `sort`演算法是穩定的，可保證會保留對等元素的相對順序。

的執行時間複雜性 `stable_sort` 取決於可用的記憶體數量，但最好的情況（提供足夠的記憶體）是，最 `O(N log N)` 壞的情況是 `O(N (log N)^2)` ，其中*N*是  =  *最後*  -  *一個*。 通常，此 `sort` 演算法的速度會明顯比更快 `stable_sort` 。

### <a name="example"></a>範例

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    stable_sort(v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    stable_sort(v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a><a name="swap"></a>調換

第一個覆寫會交換兩個物件的值。 第二個覆寫會交換兩個物件陣列之間的值。

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>參數

*左面*\
針對第一個覆寫，第一個物件會交換其內容。 針對第二個覆寫，第一個物件陣列會交換其內容。

*再*\
針對第一個覆寫，第二個物件會交換其內容。 針對第二個覆寫，第二個物件陣列會交換其內容。

### <a name="remarks"></a>備註

第一個多載設定成對個別物件作業。 第二個多載會交換兩個陣列之間的物件內容。

### <a name="example"></a>範例

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    for ( int i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }

    for ( int ii = 0 ; ii <= 4 ; ii++ )
    {
        v2.push_back( 5 );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    swap( v1, v2 );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a><a name="swap_ranges"></a>swap_ranges

將某個範圍的項目與另一個相等大小之範圍的項目交換。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
正向迭代器，指向要交換其元素之第一個範圍中的第一個位置。

*last1*\
正向迭代器，指向要交換其元素之第一個範圍中最後一個位置之後的位置。

*first2*\
正向迭代器，指向要交換其元素之第二個範圍中的第一個位置。

### <a name="return-value"></a>傳回值

正向迭代器，指向要交換其元素之第二個範圍中最後一個位置之後的位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，可透過遞增從第一個位置到達最後一個位置。 第二個範圍都必須與第一個範圍一樣大。

複雜度為線性，並已執行*last1*  -  *first1*交換。 如果正在交換相同類型之容器中的元素，則應該使用來自該容器的 `swap` 成員函式，原因是成員函式通常具有常數複雜度。

### <a name="example"></a>範例

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =4 ; ii <= 9 ; ii++ )
    {
        d1.push_back( 6 );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

    cout << "After the swap_range, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "After the swap_range deque d1 is   ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a><a name="transform"></a>轉換

將指定的函式物件應用至來源範圍中的每個項目，或是一組來自兩個來源範圍的項目，並複製函式物件的傳回值到目的範圍。

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*first1*\
輸入迭代器，定址要對其作業之第一個來源範圍中第一個元素的位置。

*last1*\
輸入迭代器，定址要對其作業之第一個來源範圍中最後一個元素之後的位置。

*first2*\
輸入迭代器，用於定址第二個來源範圍中要執行之第一個項目的位置。

*result*\
輸出迭代器，用於定址目的範圍中第一個項目的位置。

*func*\
套用至第一個來源範圍中每個元素之演算法第一版中所使用的使用者定義一元函式物件，或以正向順序成對套用至兩個來源範圍之演算法第二版中所使用的使用者定義 (UD) 二元函式物件。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址超過接收函式物件所轉換之輸出項目的目的範圍中最後一個項目的第一個位置。

### <a name="remarks"></a>備註

參考的範圍必須有效；所有指標都必須可以取值，而且在每個序列中，必須可透過遞增從第一個位置到達最後一個位置。 目的範圍必須夠大，才能包含已轉換的來源範圍。

如果在演算法的第一個版本中，將*result*設定為等於*first1* ，則來源和目的範圍會相同，而且順序會就地修改。 但*結果*可能無法處理範圍 [ `first1` + 1，）內的位置 `last1` 。

複雜度為線性，最多有（ `last1`  -  `first1` ）次比較。

### <a name="example"></a>範例

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Modifying the vector v1 in place
    transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
    cout << "The elements of the vector v1 multiplied by 2 in place gives:"
            << "\n v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using transform to multiply each element by a factor of 5
    transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a><a name="unique"></a>唯一

移除在指定範圍內彼此相鄰的重複項目。

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，定址要掃描重複移除之範圍中第一個元素的位置。

*次*\
正向迭代器，定址要掃描重複項目移除之範圍中最後一個元素之後的位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

未包含連續重複項目之修改過序列新結尾的正向迭代器，定義未移除之最後一個元素之後的位置。

### <a name="remarks"></a>備註

這兩種形式的演算法都會從一對連續的相等項目中，移除第二個重複項目。

此演算法作業很穩定，因此不會變更未刪除項目的相對順序。

參考的範圍必須有效；所有指標都必須可以取值，而且在序列中，可透過遞增從第一個位置到達最後一個位置。 此演算法不會變更序列中的元素數目 `unique` ，而且已取值但未指定超出已修改序列結尾的元素。

複雜度為線性，需要進行 `(last - first) - 1` 比較。

list 提供更具效率的成員函式 "unique"，後者的效能可能較佳。

這些演算法無法用於相關聯容器。

### <a name="example"></a>範例

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main()
{
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
            v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
    {
        v1.push_back( 4 );
    }
    v1.push_back( 7 );

    cout << "Vector v1 is ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates
    v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

    cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

    cout << "Removing adjacent duplicates from vector v1 under the\n "
            << " binary predicate mod_equal gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;

    // Remove elements if preceded by an element that was greater
    v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

    cout << "Removing adjacent elements satisfying the binary\n "
            << " predicate mod_equal from vector v1 gives ( " ;
    for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
        cout << *v1_Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a><a name="unique_copy"></a>unique_copy

將來源範圍的項目複製到目的範圍，但是彼此相鄰的重複項目除外。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>參數

*exec*\
要使用的執行原則。

*頭*\
正向迭代器，用於定址要複製之來源範圍中第一個項目的位置。

*次*\
正向迭代器，用於定址要複製之來源範圍中最後一個項目的後面一個位置。

*result*\
輸出迭代器，用於定址正在接收所移除的連續重複項目複本之目的範圍中，第一個項目的位置。

*pred*\
使用者定義的述詞函式物件，定義要接受兩個元素為對等時所要符合的條件。 二元述詞會採用兩個引數，並且在符合時傳回 **true** ，不符合時則傳回 **false** 。

### <a name="return-value"></a>傳回值

輸出迭代器，用於定址正在接收所移除的連續重複項目複本之目的範圍中，最後一個項目的後面一個位置。

### <a name="remarks"></a>備註

這兩種形式的演算法都會從一對連續的相等項目中，移除第二個重複項目。

此演算法作業很穩定，因此不會變更未刪除項目的相對順序。

參考的範圍必須有效；所有指標都必須可以取值，而且在一個序列中，可透過遞增從第一個位置到達最後一個位置。

複雜度為線性，需要（ `last`  -  `first` ）比較。

### <a name="example"></a>範例

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main() {
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
            v1_NewEnd1, v1_NewEnd2;

    int i;
    for ( i = 0 ; i <= 1 ; i++ ) {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
        v1.push_back( 4 );
    v1.push_back( 7 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 10 );

    cout << "Vector v1 is\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Copy first half to second, removing consecutive duplicates
    v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

    cout << "Copying the first half of the vector to the second half\n "
            << "while removing adjacent duplicates gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    int iv;
    for ( iv = 0 ; iv <= 7 ; iv++ )
        v1.push_back( 10 );

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
        v1.begin( ) + 14 , mod_equal );

    cout << "Copying the first half of the vector to the second half\n "
            << " removing adjacent duplicates under mod_equals gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="upper_bound"></a><a name="upper_bound"></a>upper_bound

在已排序範圍中尋找值大於指定值的第一個項目的位置，其中順序準則可由二元述詞指定。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>參數

*頭*\
所搜尋範圍中第一個元素的位置。

*次*\
所搜尋範圍中最後一個元素之後的位置。

*value*\
需要超出所傳回迭代器定址之元素值的排序範圍中的值。

*pred*\
使用者定義的比較述詞函式物件，定義其中一個專案小於另一個元素的意義。 比較述詞會採用兩個引數，並在滿意時傳回 true，而不符合時**則**傳回**false** 。

### <a name="return-value"></a>傳回值

正向迭代器，定址值大於所指定值之第一個元素的位置。

### <a name="remarks"></a>備註

參考的排序來源範圍必須有效；所有迭代器都必須可以取值，而且在序列中，必須可透過遞增從第一個位置到達最後一個位置。

已排序範圍是使用的前置條件 `upper_bound` ，而且順序準則與比較述詞所指定的相同。

`upper_bound` 不會修改範圍。

正向迭代器的實值類型必須小於比較才能建立此順序：因此若提供兩個元素，可以判斷它們相等 (任一個都不小於另一個的意義)，或者一個小於另一個。 這會導致非對等元素之間的排序。

隨機存取反覆運算器的演算法複雜度是對數，否則為線性，另一種是以與（）成正比的步驟數目 `last - first` 。

### <a name="example"></a>範例

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

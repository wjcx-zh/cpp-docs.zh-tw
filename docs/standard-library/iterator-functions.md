---
title: '&lt;iterator&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- xutility/std::advance
- xutility/std::back_inserter
- xutility/std::begin
- xutility/std::cbegin
- xutility/std::cend
- xutility/std::distance
- xutility/std::end
- xutility/std::front_inserter
- xutility/std::inserter
- xutility/std::make_checked_array_iterator
- xutility/std::make_move_iterator
- xutility/std::make_unchecked_array_iterator
- xutility/std::next
- xutility/std::prev
ms.assetid: 4a57c9a3-7e36-411f-8655-e0be2eec88e7
helpviewer_keywords:
- std::advance [C++]
- std::back_inserter [C++]
- std::begin [C++]
- std::cbegin [C++]
- std::cend [C++]
- std::distance [C++]
- std::end [C++]
- std::front_inserter [C++]
- std::inserter [C++]
- std::make_checked_array_iterator [C++]
- std::make_move_iterator [C++]
- std::make_unchecked_array_iterator [C++]
- std::next [C++]
- std::prev [C++]
ms.openlocfilehash: 615ebeedc87563eeac46c462304072ff1979040c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222312"
---
# <a name="ltiteratorgt-functions"></a>&lt;iterator&gt; 函式

## <a name="advance"></a><a name="advance"></a>過時

依指定的位置數目遞增迭代器。

```cpp
template <class InputIterator, class Distance>
    void advance(InputIterator& InIt, Distance Off);
```

### <a name="parameters"></a>參數

*初始*\
要遞增且必須符合輸入迭代器需求的迭代器。

*停止*\
整數類資料類型，可以轉換為迭代器的差異類型，並指定迭代器位置向前移的增量數目。

### <a name="remarks"></a>備註

這個前移範圍必須為非奇異，而迭代器必須是可取值或超出結尾。

如果 `InputIterator` 滿足雙向反覆運算器類型的需求，則*Off*可能是負值。 如果 `InputIterator` 是輸入或正向反覆運算器類型， *Off*就必須是非負值。

`InputIterator`滿足隨機存取反覆運算器的需求時，推進函式會有常數複雜度; 否則，它會具有線性複雜度，因此可能會耗用相當多的資源。

### <a name="example"></a>範例

```cpp
// iterator_advance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = 1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 4 );
   cout << "LPOS is advanced 4 steps forward to point"
        << " to the fifth element: "
        << *LPOS << "." << endl;

   advance ( LPOS , -3 );
   cout << "LPOS is moved 3 steps back to point to the "
        << "2nd element: " << *LPOS << "." << endl;
}
```

```Output
The list L is: ( 1 2 3 4 5 6 7 8 ).
The iterator LPOS initially points to the first element: 1.
LPOS is advanced 4 steps forward to point to the fifth element: 5.
LPOS is moved 3 steps back to point to the 2nd element: 2.
```

## <a name="back_inserter"></a><a name="back_inserter"></a>back_inserter

建立可以在指定的容器背面插入項目的迭代器。

```cpp
template <class Container>
back_insert_iterator<Container> back_inserter(Container& _Cont);
```

### <a name="parameters"></a>參數

*_Cont*\
要在其中執行背後插入的容器。

### <a name="return-value"></a>傳回值

`back_insert_iterator`與容器物件相關聯的 *_Cont*。

### <a name="remarks"></a>備註

在「C++ 標準程式庫」內，引數必須參考具有成員函式 `push_back` 的下列三個序列容器其中之一：[deque 類別](../standard-library/deque-class.md)、[list 類別](../standard-library/list-class.md) 或 [vector 類別](../standard-library/vector-class.md)。

### <a name="example"></a>範例

```cpp
// iterator_back_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 0 ; i < 3 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;
*backiter = 40;

   // Alternatively, insertions can be done with the
   // back_insert_iterator member function
   back_inserter ( vec ) = 500;
   back_inserter ( vec ) = 600;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 0 1 2 ).
After the insertions, the vector vec is: ( 0 1 2 30 40 500 600 ).
```

## <a name="begin"></a><a name="begin"></a>起點

擷取在指定的容器中第一個項目的迭代器。

```cpp
template <class Container>
auto begin(Container& cont)  `
   -> decltype(cont.begin());

template <class Container>
auto begin(const Container& cont)   `
   -> decltype(cont.begin());

template <class Ty, class Size>
Ty *begin(Ty (& array)[Size]);
```

### <a name="parameters"></a>參數

*續*\
容器。

*數列*\
`Ty` 類型的物件陣列。

### <a name="return-value"></a>傳回值

前兩個樣板函式會傳回 `cont.begin()`。 第一個函式是非常數，第二個是常數。

第三個範本函式會傳回*array*。

### <a name="example"></a>範例

需要更泛型的行為時，建議您使用這個樣板函式取代容器成員 `begin()`。

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <vector>

template <typename C> void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(begin(c), end(c), std::greater<>());
}

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        std::cout << e << " ";
    }

    std::cout << "\n";
}

int main() {
    std::vector<int> v = { 11, 34, 17, 52, 26, 13, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(v);
    reverse_sort(v);
    print(v);

    std::cout << "--\n";

    int arr[] = { 23, 70, 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 };

    print(arr);
    reverse_sort(arr);
    print(arr);
}
```

```Output
11 34 17 52 26 13 40 20 10 5 16 8 4 2 1
52 40 34 26 20 17 16 13 11 10 8 5 4 2 1
--
23 70 35 106 53 160 80 40 20 10 5 16 8 4 2 1
160 106 80 70 53 40 35 23 20 16 10 8 5 4 2 1
```

因為它會呼叫非成員版本的 `reverse_sort`，除了標準陣列之外，`begin()` 函式支援任何種類的容器。 如果 `reverse_sort` 編使用容器成員 `begin()`：

```cpp
template <typename C>
void reverse_sort(C& c) {
    using std::begin;
    using std::end;

    std::sort(c.begin(), c.end(), std::greater<>());

}
```

將陣列傳給它，會導致這個編譯器錯誤：

```Output
error C2228: left of '.begin' must have class/struct/union
```

## <a name="cbegin"></a><a name="cbegin"></a>cbegin

擷取在指定的容器中第一個項目的常數迭代器。

```cpp
template <class Container>
auto cbegin(const Container& cont)
   -> decltype(cont.begin());
```

### <a name="parameters"></a>參數

*續*\
容器或 initializer_list。

### <a name="return-value"></a>傳回值

常數 `cont.begin()`。

### <a name="remarks"></a>備註

這個函式可以與所有「C++ 標準程式庫」容器和與 [initializer_list](../standard-library/initializer-list-class.md) 搭配運作。

您可以使用此成員函式取代 `begin()` 樣板函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將視為可 `Container` 修改（非 **`const`** ）容器或 `initializer_list` 任何支援和的類型 `begin()` `cbegin()` 。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a>cend

擷取常數迭代器，指向在指定的容器中最後一個項目後面的項目。

```cpp
template <class Container>
auto cend(const Container& cont)
   -> decltype(cont.end());
```

### <a name="parameters"></a>參數

*續*\
容器或 initializer_list。

### <a name="return-value"></a>傳回值

常數 `cont.end()`。

### <a name="remarks"></a>備註

這個函式可以與所有「C++ 標準程式庫」容器和與 [initializer_list](../standard-library/initializer-list-class.md) 搭配運作。

您可以使用此成員函式來取代 [end()](../standard-library/iterator-functions.md#end) 範本函式，以確保傳回值是 `const_iterator`。 通常，它是與 [auto](../cpp/auto-cpp.md) 類型推算關鍵字一起使用，如下列範例所示。 在此範例中，請將視為可 `Container` 修改（非 **`const`** ）容器或 `initializer_list` 任何支援和的類型 `end()` `cend()` 。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

## <a name="crbegin"></a><a name="crbegin"></a>crbegin

```cpp
template <class C> constexpr auto crbegin(const C& c) -> decltype(std::rbegin(c));
```

## <a name="crend"></a><a name="crend"></a>crend

```cpp
template <class C> constexpr auto crend(const C& c) -> decltype(std::rend(c));
```

## <a name="data"></a><a name="data"></a> 資料

```cpp
template <class C> constexpr auto data(C& c) -> decltype(c.data());
template <class C> constexpr auto data(const C& c) -> decltype(c.data());
template <class T, size_t N> constexpr T* data(T (&array)[N]) noexcept;
template <class E> constexpr const E* data(initializer_list<E> il) noexcept;
```

## <a name="distance"></a><a name="distance"></a>長途電話

判斷在兩個迭代器定址的位置之間的增量數。

```cpp
template <class InputIterator>
typename iterator_traits<InputIterator>::difference_type distance(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>參數

*頭*\
要判斷與第二個迭代器之距離的第一個迭代器。

*次*\
要判斷與第一個迭代器之距離的第二個迭代器。

### <a name="return-value"></a>傳回值

*第一個*必須遞增的次數，直到*最後*一個為止。

### <a name="remarks"></a>備註

當 `InputIterator` 滿足隨機存取反覆運算器的需求時，距離函式會有常數複雜度; 否則，它會具有線性複雜度，因此可能會很耗費資源。

### <a name="example"></a>範例

```cpp
// iterator_distance.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }
   list <int>::iterator L_Iter, LPOS = L.begin ( );

   cout << "The list L is: ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   cout << "The iterator LPOS initially points to the first element: "
        << *LPOS << "." << endl;

   advance ( LPOS , 7 );
   cout << "LPOS is advanced 7 steps forward to point "
        << " to the eighth element: "
        << *LPOS << "." << endl;

   list<int>::difference_type Ldiff ;
   Ldiff = distance ( L.begin ( ) , LPOS );
   cout << "The distance from L.begin( ) to LPOS is: "
        << Ldiff << "." << endl;
}
```

```Output
The list L is: ( -2 0 2 4 6 8 10 12 14 16 ).
The iterator LPOS initially points to the first element: -2.
LPOS is advanced 7 steps forward to point  to the eighth element: 12.
The distance from L.begin( ) to LPOS is: 7.
```

## <a name="empty"></a><a name="empty"></a>空

```cpp
template <class C> constexpr auto empty(const C& c) -> decltype(c.empty());
template <class T, size_t N> constexpr bool empty(const T (&array)[N]) noexcept;
template <class E> constexpr bool empty(initializer_list<E> il) noexcept;
```

## <a name="end"></a><a name="end"></a>成品

擷取迭代器，指向在指定的容器中最後一個項目後面的項目。

```cpp
template <class Container>
auto end(Container& cont)
   -> decltype(cont.end());

template <class Container>
auto end(const Container& cont)
   -> decltype(cont.end());

template <class Ty, class Size>
Ty *end(Ty (& array)[Size]);
```

### <a name="parameters"></a>參數

*續*\
容器。

*數列*\
`Ty` 類型的物件陣列。

### <a name="return-value"></a>傳回值

前兩個樣板函式會傳回 `cont.end()` (第一個函式是非常數，而第二個函式是常數)。

第三個樣板函式會傳回 `array + Size`。

### <a name="remarks"></a>備註

如需程式碼範例，請參閱 [begin](../standard-library/iterator-functions.md#begin)。

## <a name="front_inserter"></a><a name="front_inserter"></a>front_inserter

建立可以在指定的容器前面插入項目的迭代器。

```cpp
template <class Container>
front_insert_iterator<Container> front_inserter(Container& _Cont);
```

### <a name="parameters"></a>參數

*_Cont*\
其前面要插入元素的容器物件。

### <a name="return-value"></a>傳回值

`front_insert_iterator`與容器物件相關聯的 *_Cont*。

### <a name="remarks"></a>備註

也可以使用 front_insert_iterator 類別的成員函式 [front_insert_iterator](../standard-library/front-insert-iterator-class.md#front_insert_iterator)。

在「C++ 標準程式庫」內，引數必須參考具有成員函式 `push_back` 的下列兩個序列容器其中之一：[deque 類別](../standard-library/deque-class.md) 或「list 類別」。

### <a name="example"></a>範例

```cpp
// iterator_front_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for ( i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template function to insert an element
   front_insert_iterator< list < int> > Iter(L);
*Iter = 100;

   // Alternatively, you may use the front_insert member function
   front_inserter ( L ) = 200;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( -1 0 1 2 3 4 5 6 7 8 ).
After the front insertions, the list L is:
( 200 100 -1 0 1 2 3 4 5 6 7 8 ).
```

## <a name="inserter"></a><a name="inserter"></a>插入器

Helper 範本函式，可讓您使用， `inserter(_Cont, _Where)` 而不是 `insert_iterator<Container>(_Cont, _Where)` 。

```cpp
template <class Container>
insert_iterator<Container>
inserter(
    Container& _Cont,
    typename Container::iterator _Where);
```

### <a name="parameters"></a>參數

*_Cont*\
要新增新元素的容器。

*_Where*\
找出插入點的迭代器。

### <a name="remarks"></a>備註

此範本函式會傳回[insert_iterator](../standard-library/insert-iterator-class.md#insert_iterator) `<Container>(_Cont, _Where)` 。

### <a name="example"></a>範例

```cpp
// iterator_inserter.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   list <int>::iterator L_Iter;

   list<int> L;
   for (i = 2 ; i < 5 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the template version to insert an element
   insert_iterator<list <int> > Iter( L, L.begin ( ) );
*Iter = 1;

   // Alternatively, using the member function to insert an element
   inserter ( L, L.end ( ) ) = 500;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
```

```Output
The list L is:
( 20 30 40 ).
After the insertions, the list L is:
( 1 20 30 40 500 ).
```

## <a name="make_checked_array_iterator"></a><a name="make_checked_array_iterator"></a>make_checked_array_iterator

建立其他演算法可使用的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md)。

> [!NOTE]
> 這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。

```cpp
template <class Iter>
checked_array_iterator<Iter>
    make_checked_array_iterator(
Iter Ptr,
    size_t Size,
    size_t Index = 0);
```

### <a name="parameters"></a>參數

*指標*\
目的陣列的指標。

*容量*\
目的陣列的大小。

*指數*\
陣列中選擇性的索引。

### <a name="return-value"></a>傳回值

`checked_array_iterator` 的執行個體。

### <a name="remarks"></a>備註

`make_checked_array_iterator` 函式是在 `stdext` 命名空間中定義。

這個函式會接受原始指標 (通常會導致溢出界限的顧慮)，並將其包裝在執行檢查的 [checked_array_iterator](../standard-library/checked-array-iterator-class.md) 類別中。 由於該類別已標記為已檢查，因此「C++ 標準程式庫」不會發出它的相關警告。 如需詳細資訊與程式碼範例，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

在下列範例中，會建立一個[向量](../standard-library/vector-class.md)並填入 10 個項目。 向量的內容是透過使用複製演算法複製到陣列，然後 `make_checked_array_iterator` 會用來指定目的。 接著界限故意違規檢查，以便觸發偵錯判斷提示失敗。

```cpp
// make_checked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_checked_array_iterator
#include <memory> // std::make_unique
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    // Old-school but not exception safe, favor make_unique<int[]>
    // int* dest = new int[dest_size];
    unique_ptr<int[]> updest = make_unique<int[]>(dest_size);
    int* dest = updest.get(); // get a raw pointer for the demo

    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    // Add another element to the vector to force an overrun.
    v.push_back(10);
    // The next line causes a debug assertion when it executes.
    copy(v.begin(), v.end(), stdext::make_checked_array_iterator(dest, dest_size));
}
```

## <a name="make_move_iterator"></a><a name="make_move_iterator"></a>make_move_iterator

建立一個包含所提供迭代器作為`stored`迭代器的 `move iterator`。

```cpp
template <class Iterator>
move_iterator<Iterator>
make_move_iterator(const Iterator& _It);
```

### <a name="parameters"></a>參數

*_It*\
儲存在新移動迭代器中的迭代器。

### <a name="remarks"></a>備註

此範本函式會傳回 `move_iterator` `<Iterator>(_It)`。

## <a name="make_unchecked_array_iterator"></a><a name="make_unchecked_array_iterator"></a>make_unchecked_array_iterator

建立其他演算法可使用的 [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)。

> [!NOTE]
> 這個函式是「C++ 標準程式庫」的 Microsoft 擴充功能。 透過使用這個函式實作的程式碼不可移植到不支援此 Microsoft 擴充功能的 C++ Standard 建置環境。

```cpp
template <class Iter>
unchecked_array_iterator<Iter>
    make_unchecked_array_iterator(Iter Ptr);
```

### <a name="parameters"></a>參數

*指標*\
目的陣列的指標。

### <a name="return-value"></a>傳回值

`unchecked_array_iterator` 的執行個體。

### <a name="remarks"></a>備註

`make_unchecked_array_iterator` 函式是在 `stdext` 命名空間中定義。

這個函式會使用原始指標，並將它包裝在不執行任何檢查的類別中，因此會最佳化到極精簡的程度，但它也會關閉編譯器警告，例如 [C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)。 因此，這是處理未檢查指標警告的目標方式，而不需要全域關閉警告訊息或產生檢查成本。 如需詳細資訊與程式碼範例，請參閱[已檢查的迭代器](../standard-library/checked-iterators.md)。

### <a name="example"></a>範例

在下列範例中，會建立一個[向量](../standard-library/vector-class.md)並填入 10 個項目。 向量的內容是透過使用複製演算法複製到陣列，然後 `make_unchecked_array_iterator` 會用來指定目的。

```cpp
// make_unchecked_array_iterator.cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iterator> // stdext::make_unchecked_array_iterator
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const size_t dest_size = 10;
    int *dest = new int[dest_size];
    vector<int> v;

    for (int i = 0; i < dest_size; ++i) {
        v.push_back(i);
    }
    print("vector v: ", v);

    // COMPILER WARNING SILENCED: stdext::unchecked_array_iterator is marked as checked in debug mode
    // (it performs no checking, so an overrun will trigger undefined behavior)
    copy(v.begin(), v.end(), stdext::make_unchecked_array_iterator(dest));

    cout << "int array dest: ";
    for (int i = 0; i < dest_size; ++i) {
        cout << dest[i] << " ";
    }
    cout << endl;

    delete[] dest;
}
```

## <a name="next"></a><a name="next"></a>下一個

反覆運算指定的次數，並傳回新的迭代器位置。

```cpp
template <class InputIterator>
InputIterator next(
    InputIterator first,
    typename iterator_traits<InputIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>參數

*頭*\
目前位置。

*_Off*\
要逐一查看的次數。

### <a name="return-value"></a>傳回值

在反覆運算 *_Off*次之後，傳回新的反覆運算器位置。

### <a name="remarks"></a>備註

此範本函式會傳回 `next` 遞增的 *_Off*次

## <a name="prev"></a><a name="prev"></a>前

以反向方向反覆運算指定的次數，並傳回新的迭代器位置。

```cpp
template <class BidirectionalIterator>
BidirectionalIterator prev(
    BidirectionalIterator first,
    typename iterator_traits<BidirectionalIterator>::difference_type _Off = 1);
```

### <a name="parameters"></a>參數

*頭*\
目前位置。

*_Off*\
要逐一查看的次數。

### <a name="remarks"></a>備註

此範本函式會傳回遞減 `off` 次後的 `next`。

## <a name="rbegin"></a><a name="rbegin"></a>rbegin

```cpp
template <class C> constexpr auto rbegin(C& c) -> decltype(c.rbegin());
template <class C> constexpr auto rbegin(const C& c) -> decltype(c.rbegin());
```

## <a name="rend"></a><a name="rend"></a>rend

```cpp
template <class C> constexpr auto rend(C& c) -> decltype(c.rend());
template <class C> constexpr auto rend(const C& c) -> decltype(c.rend());
```

## <a name="size"></a><a name="size"></a>容量

```cpp
template <class C> constexpr auto size(const C& c) -> decltype(c.size());
template <class T, size_t N> constexpr size_t size(const T (&array)[N]) noexcept;
```

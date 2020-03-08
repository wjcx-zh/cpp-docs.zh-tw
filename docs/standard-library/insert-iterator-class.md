---
title: insert_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- iterator/std::insert_iterator
- iterator/std::insert_iterator::container_type
- iterator/std::insert_iterator::reference
helpviewer_keywords:
- std::insert_iterator [C++]
- std::insert_iterator [C++], container_type
- std::insert_iterator [C++], reference
ms.assetid: d5d86405-872e-4e3b-9e68-c69a2b7e8221
ms.openlocfilehash: 15041e21b53c29aedda831fd73b37a65e57a3680
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78874034"
---
# <a name="insert_iterator-class"></a>insert_iterator 類別

描述滿足輸出迭代器需求的迭代器配接器。 它在序列中插入項目 (而不是覆寫)，因此其語意不同於 C++ 序列容器和關聯容器的迭代器所提供的覆寫語意。 `insert_iterator` 類別是根據所調整容器的類型樣板化。

## <a name="syntax"></a>語法

```cpp
template <class Container>
class insert_iterator;
```

### <a name="parameters"></a>參數

*容器*\
容器的類型，`insert_iterator` 將在其中插入項目。

## <a name="remarks"></a>備註

`Container` 類型的容器必須滿足可變大小容器的需求，而且具有兩個引數插入成員函式，其中參數的類型為 `Container::iterator` 和 `Container::value_type`，而且會傳回 `Container::iterator`的類型。 「C++ 標準程式庫」序列容器和已排序關聯容器可滿足這些需求，並可調整來與 `insert_iterator` 搭配使用。 對於關聯容器，位置引數視為提示，可能會根據提示品質改善或降低效能。 `insert_iterator` 一定要以其容器初始化。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[insert_iterator](#insert_iterator)|建構 `insert_iterator`，將項目插入容器中的指定位置。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[container_type](#container_type)|類型，表示要執行一般插入的容器。|
|[reference](#reference)|類型，提供關聯容器控制之序列中項目的參考。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式 * `i` = `x` 以進行一般插入。|
|[operator++](#op_add_add)|將 `insert_iterator` 遞增至可儲存值的下一個位置。|
|[operator=](#op_eq)|指派運算子，用來實作輸出迭代器運算式 * `i` = `x` 以進行一般插入。|

## <a name="requirements"></a>需求

**標頭**：\<iterator>

**命名空間:** std

## <a name="container_type"></a>  insert_iterator::container_type

類型，表示要執行一般插入的容器。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Container* 同義。

### <a name="example"></a>範例

```cpp
// insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   insert_iterator<list<int> >::container_type L2 = L1;
   inserter ( L2, L2.end ( ) ) = 20;
   inserter ( L2, L2.end ( ) ) = 10;
   inserter ( L2, L2.begin ( ) ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 20 10 ).
*/
```

## <a name="insert_iterator"></a>  insert_iterator::insert_iterator

建構 `insert_iterator`，將項目插入容器中的指定位置。

```cpp
insert_iterator(Container& _Cont, typename Container::iterator _It);
```

### <a name="parameters"></a>參數

*_Cont*\
`insert_iterator` 要在其中插入元素的容器。

*_It*\
插入的位置。

### <a name="remarks"></a>備註

所有容器的 insert 成員函式都會由 `insert_iterator` 呼叫。 針對關聯容器，位置參數只是建議。 inserter 函式提供一個插入到值中的便利方式。

### <a name="example"></a>範例

```cpp
// insert_iterator_insert_iterator.cpp
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
   for (i = 1 ; i < 4 ; ++i )
   {
      L.push_back ( 10 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   inserter ( L, L.begin ( ) ) = 2;

   // Alternatively, you may use the template version
   insert_iterator< list < int> > Iter(L, L.end ( ) );
*Iter = 300;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( 10 20 30 ).
After the insertions, the list L is:
( 2 10 20 30 300 ).
*/
```

## <a name="op_star"></a>  insert_iterator::operator*

對傳回所定址之元素的插入迭代器進行取值。

```cpp
insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>傳回值

此成員函式會傳回所定址之元素的值。

### <a name="remarks"></a>備註

用來實作輸出迭代器運算式 **\*Iter** = **value**。 如果 `Iter` 是定址序列中專案的反覆運算器，則 **\*Iter** = **值**會以值取代該元素，而且不會變更序列中的元素總數。

### <a name="example"></a>範例

```cpp
// insert_iterator_op_deref.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="op_add_add"></a>  insert_iterator::operator++

將 `insert_iterator` 遞增至可儲存值的下一個位置。

```cpp
insert_iterator<Container>& operator++();

insert_iterator<Container> operator++(int);
```

### <a name="parameters"></a>參數

`insert_iterator`，定址對象為可儲存值的下一個位置。

### <a name="remarks"></a>備註

preincrementation 和 postincrementation 運算子都會傳回相同的結果。

### <a name="example"></a>範例

```cpp
// insert_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 5 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   insert_iterator<vector<int> > ii ( vec, vec.begin ( ) );
*ii = 30;
   ii++;
*ii = 40;
   ii++;
*ii = 50;

   cout << "After the insertions, the vector vec becomes:\n ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The vector vec is:
( 1 2 3 4 ).
After the insertions, the vector vec becomes:
( 30 40 50 1 2 3 4 ).
*/
```

## <a name="op_eq"></a>  insert_iterator::operator=

將值插入到容器中並傳回已更新成指向新元素的迭代器。

```cpp
insert_iterator<Container>& operator=(
    typename Container::const_reference val,);

insert_iterator<Container>& operator=(
    typename Container::value_type&& val);
```

### <a name="parameters"></a>參數

*val*\
要指派給容器的值。

### <a name="return-value"></a>傳回值

對插入到容器中之元素的參考。

### <a name="remarks"></a>備註

第一個成員運算子會評估

`Iter = container->insert(Iter, val)`;

`++Iter;`

然後傳回 `*this`。

第二個成員運算子會評估

`Iter = container->insert(Iter, std::move(val));`

`++Iter;`

然後傳回 `*this`。

### <a name="example"></a>範例

```cpp
// insert_iterator_op_assign.cpp
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
   for (i = 0 ; i < 4 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The original list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;

   insert_iterator< list < int> > Iter(L, L.begin ( ) );
*Iter = 10;
*Iter = 20;
*Iter = 30;

   cout << "After the insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++ )
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The original list L is:
( 0 2 4 6 ).
After the insertions, the list L is:
( 10 20 30 0 2 4 6 ).
*/
```

## <a name="reference"></a>  insert_iterator::reference

類型，提供關聯容器控制之序列中項目的參考。

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>備註

此類型描述相關聯容器所控制序列之元素的參考。

### <a name="example"></a>範例

```cpp
// insert_iterator_container_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   insert_iterator<list<int> > iivIter( L , L.begin ( ) );
*iivIter = 10;
*iivIter = 20;
*iivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++ )
      cout << *LIter << " ";
   cout << ")." << endl;

   insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 10 20 30 ).
The first element in the list L is: 10.
*/
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)

---
title: front_insert_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iterator/std::front_insert_iterator
- iterator/std::front_insert_iterator::container_type
- iterator/std::front_insert_iterator::reference
dev_langs:
- C++
helpviewer_keywords:
- std::front_insert_iterator [C++]
- std::front_insert_iterator [C++], container_type
- std::front_insert_iterator [C++], reference
ms.assetid: a9a9c075-136a-4419-928b-c4871afa033c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcd8d623b4ce16f7f7af671d06dae568ec2a53d1
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44318192"
---
# <a name="frontinsertiterator-class"></a>front_insert_iterator 類別

描述滿足輸出迭代器需求的迭代器配接器。 它在序列前端插入項目 (而不是覆寫)，因此其語意不同於 C++ 序列容器的迭代器所提供的覆寫語意。 `front_insert_iterator` 類別是根據容器的類型樣板化。

## <a name="syntax"></a>語法

```cpp
template <class Container>
class front_insert_iterator;
```

### <a name="parameters"></a>參數

*容器*<br/>
容器的類型，其項目前端要由 `front_insert_iterator` 插入。

## <a name="remarks"></a>備註

容器必須符合是否可以在平攤常數時間將項目插入於序列開頭的前端插入序列需求。 [deque 類別](../standard-library/deque-class.md)和 [list 類別](../standard-library/list-class.md)所定義的 C++ 標準程式庫序列容器，可提供所需的 `push_front` 成員函式，並滿足這些需求。 相反地，[vector 類別](../standard-library/vector-class.md)所定義的序列容器不滿足這些需求，亦無法調整以搭配 `front_insert_iterator` 使用。 `front_insert_iterator` 一定要以其容器初始化。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[front_insert_iterator](#front_insert_iterator)|建立可以在指定的容器物件前面插入項目的迭代器。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[container_type](#container_type)|類型，表示要執行前端插入的容器。|
|[reference](#reference)|類型，提供關聯容器控制之序列中項目的參考。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式\* `i`  =  `x`以進行前端插入。|
|[operator++](#op_add_add)|將 `front_insert_iterator` 遞增至可儲存值的下一個位置。|
|[operator=](#op_eq)|指派運算子，用來實作輸出迭代器運算式\* `i`  =  `x`以進行前端插入。|

## <a name="requirements"></a>需求

**標頭**：\<iterator>

**命名空間：** std

## <a name="container_type"></a>  front_insert_iterator::container_type

類型，表示要執行前端插入的容器。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Container* 同義。

### <a name="example"></a>範例

```cpp
// front_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> >::container_type L2 = L1;
   front_inserter ( L2 ) = 20;
   front_inserter ( L2 ) = 10;
   front_inserter ( L2 ) = 40;

   list <int>::iterator vIter;
   cout << "The list L2 is: ( ";
   for ( vIter = L2.begin ( ) ; vIter != L2.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L2 is: ( 40 10 20 ).
*/
```

## <a name="front_insert_iterator"></a>  front_insert_iterator::front_insert_iterator

建立可以在指定的容器物件前面插入項目的迭代器。

```cpp
explicit front_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>參數

*_Cont*<br/>
`front_insert_iterator` 要插入元素的目標容器物件。

### <a name="return-value"></a>傳回值

參數容器物件的 `front_insert_iterator`。

### <a name="example"></a>範例

```cpp
// front_insert_iterator_front_insert_iterator.cpp
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
   for (i = -1 ; i < 9 ; ++i )
   {
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   // Using the member function to insert an element
   front_inserter ( L ) = 20;

   // Alternatively, one may use the template function
   front_insert_iterator< list < int> > Iter(L);
*Iter = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="op_star"></a>  front_insert_iterator:: operator\*

可對傳回所定址之元素的插入迭代器進行取值。

```cpp
front_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>傳回值

此成員函式會傳回所定址之元素的值。

### <a name="remarks"></a>備註

用來實作輸出迭代器運算式 **\*Iter** = **value**。 如果`Iter`是迭代器，定址的項目順序，然後 **\*Iter** = **值**會以值取代該元素，並不會變更總數序列中的項目。

### <a name="example"></a>範例

```cpp
// front_insert_iterator_deref.cpp
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
      L.push_back ( 2 * i );
   }

   cout << "The list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;

   front_insert_iterator< list < int> > Iter(L);
*Iter = 20;

   // Alternatively, you may use
   front_inserter ( L ) = 30;

   cout << "After the front insertions, the list L is:\n ( ";
   for ( L_Iter = L.begin( ) ; L_Iter != L.end( ); L_Iter++)
      cout << *L_Iter << " ";
   cout << ")." << endl;
}
/* Output:
The list L is:
( -2 0 2 4 6 8 10 12 14 16 ).
After the front insertions, the list L is:
( 30 20 -2 0 2 4 6 8 10 12 14 16 ).
*/
```

## <a name="op_add_add"></a>  front_insert_iterator::operator++

將 `back_insert_iterator` 遞增至可儲存值的下一個位置。

```cpp
front_insert_iterator<Container>& operator++();

front_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>傳回值

`front_insert_iterator`，定址可儲存值的下一個位置。

### <a name="remarks"></a>備註

preincrementation 和 postincrementation 運算子都會傳回相同的結果。

### <a name="example"></a>範例

```cpp
// front_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="op_eq"></a>  front_insert_iterator::operator=

將值附加 (推送) 到容器前端。

```cpp
front_insert_iterator<Container>& operator=(typename Container::const_reference val);

front_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>參數

*val*<br/>
要指派給容器的值。

### <a name="return-value"></a>傳回值

插入容器前端之最後一個元素的參考。

### <a name="remarks"></a>備註

第一個成員運算子會評估 `container.push_front( val)`，然後傳回 `*this`。

在第二個成員運算子會評估

`container->push_front((typename Container::value_type&&) val)`,

然後傳回 `*this`。

### <a name="example"></a>範例

```cpp
// front_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L1;
   front_insert_iterator<list<int> > iter ( L1 );
*iter = 10;
   iter++;
*iter = 20;
   iter++;
*iter = 30;
   iter++;

   list <int>::iterator vIter;
   cout << "The list L1 is: ( ";
   for ( vIter = L1.begin ( ) ; vIter != L1.end ( ); vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
/* Output:
The list L1 is: ( 30 20 10 ).
*/
```

## <a name="reference"></a>  front_insert_iterator::reference

類型，提供關聯容器控制之序列中項目的參考。

```cpp
typedef typename Container::reference reference;
```

### <a name="example"></a>範例

```cpp
// front_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   list<int> L;
   front_insert_iterator<list<int> > fiivIter( L );
*fiivIter = 10;
*fiivIter = 20;
*fiivIter = 30;

   list<int>::iterator LIter;
   cout << "The list L is: ( ";
   for ( LIter = L.begin ( ) ; LIter != L.end ( ); LIter++)
      cout << *LIter << " ";
   cout << ")." << endl;

   front_insert_iterator<list<int> >::reference
        RefFirst = *(L.begin ( ));
   cout << "The first element in the list L is: "
        << RefFirst << "." << endl;
}
/* Output:
The list L is: ( 30 20 10 ).
The first element in the list L is: 30.
*/
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

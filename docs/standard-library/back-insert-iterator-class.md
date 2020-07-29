---
title: back_insert_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- iterator/std::back_insert_iterator
- iterator/std::back_insert_iterator::container_type
- iterator/std::back_insert_iterator::reference
helpviewer_keywords:
- std::back_insert_iterator [C++]
- std::back_insert_iterator [C++], container_type
- std::back_insert_iterator [C++], reference
ms.assetid: a1ee07f2-cf9f-46a1-8608-cfaf207f9713
ms.openlocfilehash: 0a518253c28d89de6eeed51e152e11bfcb8bb969
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203873"
---
# <a name="back_insert_iterator-class"></a>back_insert_iterator 類別

描述滿足輸出迭代器需求的迭代器配接器。 它在序列後端插入項目 (而不是覆寫)，因此其語意不同於 C++ 序列容器的迭代器所提供的覆寫語意。 `back_insert_iterator` 類別是根據容器的類型樣板化。

## <a name="syntax"></a>語法

```cpp
template <class Container>
class back_insert_iterator;
```

### <a name="parameters"></a>參數

*箱*\
容器的類型，其項目後端要由 `back_insert_iterator` 插入。

## <a name="remarks"></a>備註

容器必須符合是否可以在平攤常數時間將項目插入於序列結尾的後端插入序列需求。 [deque 類別](../standard-library/deque-class.md)、[list 類別](../standard-library/list-class.md)和 [vector 類別](../standard-library/vector-class.md)所定義的 C++ 標準程式庫序列容器提供需要的 `push_back` 成員函式且滿足這些需求。 這三個容器以及字串都可以調整，以搭配 `back_insert_iterator` 使用。 `back_insert_iterator` 一定要以其容器初始化。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[back_insert_iterator](#back_insert_iterator)|建構 `back_insert_iterator`，在容器的最後一個項目之後插入項目。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[container_type](#container_type)|類型，提供 `back_insert_iterator` 的容器。|
|[reference](#reference)|類型，提供 `back_insert_iterator` 的參考。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[操作](#op_star)|取值運算子，用來為 \* `i`  =  `x` 後置插入執行輸出反覆運算器運算式。|
|[operator + +](#op_add_add)|將 `back_insert_iterator` 遞增至可儲存值的下一個位置。|
|[operator =](#op_eq)|指派運算子，用來 \* `i`  =  `x` 針對後置插入執行輸出反覆運算器運算式。|

## <a name="requirements"></a>需求

**標頭**：\<iterator>

**命名空間：** std

## <a name="back_insert_iteratorback_insert_iterator"></a><a name="back_insert_iterator"></a>back_insert_iterator：： back_insert_iterator

建構 `back_insert_iterator`，在容器的最後一個項目之後插入項目。

```cpp
explicit back_insert_iterator(Container& _Cont);
```

### <a name="parameters"></a>參數

*_Cont*\
`back_insert_iterator` 要在其中插入元素的容器。

### <a name="return-value"></a>傳回值

參數容器的 `back_insert_iterator`。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_back_insert_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for ( i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The initial vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   // Insertions with member function
   back_inserter ( vec ) = 40;
   back_inserter ( vec ) = 50;

   // Alternatively, insertions can be done with template function
   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 600;
   backiter++;
*backiter = 700;

   cout << "After the insertions, the vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The initial vector vec is: ( 1 2 3 ).
After the insertions, the vector vec is: ( 1 2 3 40 50 600 700 ).
```

## <a name="back_insert_iteratorcontainer_type"></a><a name="container_type"></a>back_insert_iterator：： container_type

類型，提供 `back_insert_iterator` 的容器。

```cpp
typedef Container
container_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 **Container** 同義。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_container_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back (  i );
   }

   vector <int>::iterator vIter;
   cout << "The original vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::container_type vec1 = vec;
   back_inserter ( vec1 ) = 40;

   cout << "After the insertion, the vector is: ( ";
   for ( vIter = vec1.begin ( ) ; vIter != vec1.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector vec is: ( 1 2 3 ).
After the insertion, the vector is: ( 1 2 3 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_star"></a>back_insert_iterator：： operator\*

取值運算子，用來執行輸出反覆運算器運算式 \* *i*  =  *x*。

```cpp
back_insert_iterator<Container>& operator*();
```

### <a name="return-value"></a>傳回值

插入容器後端之元素的參考。

### <a name="remarks"></a>備註

用來執行輸出反覆運算器運算式** \* Iter**  =  **值**。 如果 **Iter** 是以序列中元素為定址對象的迭代器，則 **\*Iter** = **value** 會以值取代該元素，而不會變更序列中的元素總數。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_back_insert.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
After the insertions, the vector vec becomes: ( 1 2 3 10 20 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_add_add"></a>back_insert_iterator：： operator + +

將 `back_insert_iterator` 遞增至可儲存值的下一個位置。

```cpp
back_insert_iterator<Container>& operator++();
back_insert_iterator<Container> operator++(int);
```

### <a name="return-value"></a>傳回值

`back_insert_iterator`，定址可儲存值的下一個位置。

### <a name="remarks"></a>備註

preincrementation 和 postincrementation 運算子都會傳回相同的結果。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_op_incre.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 3 ; ++i )
   {
      vec.push_back ( 10 * i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 30;
   backiter++;      // Increment to the next element
*backiter = 40;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The vector vec is: ( 10 20 ).
After the insertions, the vector vec becomes: ( 10 20 30 40 ).
```

## <a name="back_insert_iteratoroperator"></a><a name="op_eq"></a>back_insert_iterator：： operator =

將值附加或推送到容器後端。

```cpp
back_insert_iterator<Container>& operator=(typename Container::const_reference val);
back_insert_iterator<Container>& operator=(typename Container::value_type&& val);
```

### <a name="parameters"></a>參數

*初始值*\
要插入容器的值。

### <a name="return-value"></a>傳回值

插入容器後端之最後一個元素的參考。

### <a name="remarks"></a>備註

第一個成員運算子會評估 `Container.push_back( val)`，

然後傳回 **`*this`** 。 在第二個成員運算子會評估

`container->push_back((typename Container::value_type&&)val)`,

然後傳回 **`*this`** 。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> > backiter ( vec );
*backiter = 10;
   backiter++;      // Increment to the next element
*backiter = 20;
   backiter++;

   cout << "After the insertions, the vector vec becomes: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

## <a name="back_insert_iteratorreference"></a><a name="reference"></a>back_insert_iterator：： reference

類型，提供 `back_insert_iterator` 的參考。

```cpp
typedef typename Container::reference reference;
```

### <a name="remarks"></a>備註

此類型描述相關聯容器所控制序列之元素的參考。

### <a name="example"></a>範例

```cpp
// back_insert_iterator_reference.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   vector<int> vec;
   for (i = 1 ; i < 4 ; ++i )
   {
      vec.push_back ( i );
   }

   vector <int>::iterator vIter;
   cout << "The vector vec is: ( ";
   for ( vIter = vec.begin ( ) ; vIter != vec.end ( ); vIter++)
      cout << *vIter << " ";
   cout << ")." << endl;

   back_insert_iterator<vector<int> >::reference
        RefLast = *(vec.end ( ) - 1 );
   cout << "The last element in the vector vec is: "
        << RefLast << "." << endl;
}
```

```Output
The vector vec is: ( 1 2 3 ).
The last element in the vector vec is: 3.
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

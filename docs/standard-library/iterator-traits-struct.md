---
title: iterator_traits 結構
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator_traits
helpviewer_keywords:
- iterator_traits struct
- iterator_traits class
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
ms.openlocfilehash: 924ca5ae1d32753bbe315252d942425712962639
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689456"
---
# <a name="iterator_traits-struct"></a>iterator_traits 結構

範本協助程式結構，用來指定迭代器應有的所有重要類型定義。

## <a name="syntax"></a>語法

```cpp
struct iterator_traits {
   typedef typename Iterator::iterator_category iterator_category;
   typedef typename Iterator::value_type value_type;
   typedef typename Iterator::difference_type difference_type;
   typedef difference_type distance_type;
   typedef typename Iterator::pointer pointer;
   typedef typename Iterator::reference reference;
   };
```

## <a name="remarks"></a>備註

範本結構會定義成員類型

- `iterator_category`： `Iterator::iterator_category` 的同義字。

- `value_type`： `Iterator::value_type` 的同義字。

- `difference_type`： `Iterator::difference_type` 的同義字。

- `distance_type`： `Iterator::difference_type.` 的同義字

- `pointer`： `Iterator::pointer` 的同義字。

- `reference`： `Iterator::reference` 的同義字。

部分特製化會判斷與類型**類型**的物件指標相關聯的關鍵類型<strong>\*</strong>或**const 類型** <strong>\*</strong>。

在這項實作中，您也可以使用數個不利用部分特製化的範本函式：

```cpp
template <class Category, class Type, class Diff>
C _Iter_cat(const iterator<Category, Ty, Diff>&);

template <class Ty>
random_access_iterator_tag _Iter_cat(const Ty *);

template <class Category, class Ty, class Diff>
Ty *val_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
Ty *val_type(const Ty *);

template <class Category, class Ty, class Diff>
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);

template <class Ty>
ptrdiff_t *_Dist_type(const Ty *);
```

這會更間接地決定數個相同類型。 您可以在函式呼叫上使用這些函式作為引數。 其唯一目的是要提供有用的類別樣板參數給所呼叫的函式。

## <a name="example"></a>範例

```cpp
// iterator_traits.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <vector>
#include <list>

using namespace std;

template< class it >
void
function( it i1, it i2 )
{
   iterator_traits<it>::iterator_category cat;
   cout << typeid( cat ).name( ) << endl;
   while ( i1 != i2 )
   {
      iterator_traits<it>::value_type x;
      x = *i1;
      cout << x << " ";
      i1++;
   };
   cout << endl;
};

int main( )
{
   vector<char> vc( 10,'a' );
   list<int> li( 10 );
   function( vc.begin( ), vc.end( ) );
   function( li.begin( ), li.end( ) );
}
/* Output:
struct std::random_access_iterator_tag
a a a a a a a a a a
struct std::bidirectional_iterator_tag
0 0 0 0 0 0 0 0 0 0
*/
```

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間:** std

## <a name="see-also"></a>請參閱

[\<iterator>](../standard-library/iterator.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

---
title: ostream_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: 97367c19d0b1bdb4b9c16d5d12621210c8562485
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224665"
---
# <a name="ostream_iterator-class"></a>ostream_iterator 類別

類別樣板 ostream_iterator 描述輸出反覆運算器物件，它會使用解壓縮將後續的元素寫入輸出資料流程 `operator <<` 。

## <a name="syntax"></a>語法

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>參數

*型*\
要插入至輸出資料流的物件類型。

*CharType*\
類型，表示 `ostream_iterator` 的字元類型。 這個引數是選擇性的，而且預設值是 **`char`** 。

*共同*\
類型，表示 `ostream_iterator` 的字元類型。 這個引數是選擇性的，而且預設值是 `char_traits` \< *CharType> . *

ostream_iterator 類別必須符合輸出迭代器的需求。 使用 `ostream_iterator`，演算法可以直接寫入輸出資料流。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[ostream_iterator](#ostream_iterator)|建構初始化和分隔以寫入輸出資料流的 `ostream_iterator`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，提供 `ostream_iterator` 的字元類型。|
|[ostream_type](#ostream_type)|類型，提供 `ostream_iterator` 的資料流類型。|
|[traits_type](#traits_type)|類型，提供 `ostream_iterator` 的字元特性類型。|

### <a name="operators"></a>操作員

|運算子|說明|
|-|-|
|[操作](#op_star)|取值運算子，用來執行輸出反覆運算器運算式 \* `i`  =  `x` 。|
|[operator + +](#op_add_add)|無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。|
|[operator =](#op_eq)|指派運算子，用來執行輸出反覆運算器運算式 \* `i`  =  `x` 以寫入輸出資料流程。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator：： char_type

類型，提供迭代器的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

### <a name="example"></a>範例

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator：： operator *

取值運算子，用來執行輸出反覆運算器運算式 \* *ii*  =  *x*。

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

必須滿足之輸出反覆運算器的需求， `ostream_iterator` 只要求運算式 \* *ii*  =  *t*有效，且本身不會顯示 **`operator`** 或的任何內容 `operator=` 。 此實作為中的成員運算子會傳回** \* this**。

### <a name="example"></a>範例

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator：： operator + +

無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

這些成員運算子都會傳回** \* 此**。

### <a name="example"></a>範例

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator：： operator =

指派運算子，用來執行用於 \* `i`  =  `x` 寫入輸出資料流程的 output_iterator 運算式。

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>參數

*初始值*\
要插入至輸出資料流的 `Type` 類型物件值。

### <a name="return-value"></a>傳回值

運算子會將*val*插入與物件相關聯的輸出資料流程中，後面接著[ostream_iterator](#ostream_iterator)的函式中指定的分隔符號（如果有的話），然後傳回的參考 `ostream_iterator` 。

### <a name="remarks"></a>備註

必須滿足之輸出反覆運算器的需求， `ostream_iterator` 只需要運算式 \* `ii`  =  `t` 有效，且本身不會顯示任何運算子或 operator =。 這個成員運算子會傳回 **`*this`** 。

### <a name="example"></a>範例

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator：： ostream_iterator

建構初始化和分隔以寫入輸出資料流的 `ostream_iterator`。

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>參數

*_Ostr*\
要逐一查看之類型 [ostream_iterator::ostream_type](#ostream_type) 的輸出資料流。

*_Delimiter*\
要插入至輸出資料流值之間的分隔符號。

### <a name="remarks"></a>備註

第一個建構函式會使用 `&_Ostr` 初始化輸出資料流指標。 分隔符號字串指標指定為空字串。

第二個函式會使用初始化輸出資料流程指標 `&_Ostr` ，並使用 *_Delimiter*的分隔符號字串指標。

### <a name="example"></a>範例

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator：： ostream_type

類型，提供迭代器的資料流類型。

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>備註

此類型是 basic_ostream 的同義字[basic_ostream](../standard-library/basic-ostream-class.md) <  `CharType` ，> 是 iostream 階層的 `Traits` 資料流程類別，定義可以用來寫入的物件。

### <a name="example"></a>範例

如需如何宣告及使用 `ostream_type` 的範例，請參閱 [ostream_iterator](#ostream_iterator)。

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator：： traits_type

類型，提供迭代器的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Traits` 的同義字。

### <a name="example"></a>範例

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

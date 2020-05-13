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
ms.openlocfilehash: a0c794fe2ff7897bcb6d6412613689100a977589
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373590"
---
# <a name="ostream_iterator-class"></a>ostream_iterator 類別

類範本ostream_iterator描述一個輸出反覆運算器物件,該物件使用提取`operator <<`將連續元素寫入輸出流。

## <a name="syntax"></a>語法

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>參數

*類型*\
要插入至輸出資料流的物件類型。

*字元類型*\
類型，表示 `ostream_iterator` 的字元類型。 這裡參數是選擇的預設值為**char**。

*性狀*\
類型，表示 `ostream_iterator` 的字元類型。 這個引數是選用引數，且預設值是 `char_traits`\< *CharType>*。

ostream_iterator 類別必須符合輸出迭代器的需求。 使用 `ostream_iterator`，演算法可以直接寫入輸出資料流。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[ostream_iterator](#ostream_iterator)|建構初始化和分隔以寫入輸出資料流的 `ostream_iterator`。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，提供 `ostream_iterator` 的字元類型。|
|[ostream_type](#ostream_type)|類型，提供 `ostream_iterator` 的資料流類型。|
|[traits_type](#traits_type)|類型，提供 `ostream_iterator` 的字元特性類型。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_star)|\*`i` = 用於實現`x`輸出反覆運算器表達式的取消引用運算符。|
|[運算子*](#op_add_add)|無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。|
|[運算子*](#op_eq)|用於實現用於寫入輸出流的輸出反覆運算\*`i` = `x`器表達式的分配運算符。|

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator:char_type

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

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator::操作員*

用於實現輸出\*反覆運算器運算*式 ii* = *x*的取消引用運算符。

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

`ostream_iterator`必須滿足的輸出反覆運算器\*的要求只需要運算*式 ii* = *t*有效,並且對**運算符**`operator=`或運算符 本身不說任何內容。 此實作的成員運算符傳回**\*此**。

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

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator::操作員*

無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

這些成員運算子都傳回**\*此**。

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

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator::操作員*

\*`i` = 用於實現`x`output_iterator表達式以寫入輸出流的賦值運算符。

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>參數

*瓦爾*\
要插入至輸出資料流的 `Type` 類型物件值。

### <a name="return-value"></a>傳回值

運算元將*val*插入到與物件關聯的輸出流中,然後是[ostream_iterator建構函數](#ostream_iterator)中指定的分隔符(如果有),然後`ostream_iterator`返回對的引用。

### <a name="remarks"></a>備註

`ostream_iterator`必須滿足的輸出反覆運算器的要求只需要表達式\*`ii` = `t`有效,並且對運算符或運算符* 本身不說任何內容。 此成員運算子會傳回 `*this`。

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

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator:ostream_iterator

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

第二個建構函數,`&_Ostr`或是分隔符元字串指標初始化輸出流指標 *,_Delimiter*。

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

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator:ostream_type

類型，提供迭代器的資料流類型。

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>備註

該類型是[basic_ostream,>](../standard-library/basic-ostream-class.md)< `CharType``Traits`的同義詞,iostream層次結構的流類,用於定義可用於寫入的物件。

### <a name="example"></a>範例

如需如何宣告及使用 `ostream_type` 的範例，請參閱 [ostream_iterator](#ostream_iterator)。

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator:traits_type

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

[\<反覆運算器>](../standard-library/iterator.md)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++標準函式庫參考](../standard-library/cpp-standard-library-reference.md)

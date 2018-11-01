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
ms.openlocfilehash: 6a065a100faf5ea40be161e980de2913add917fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449217"
---
# <a name="ostreamiterator-class"></a>ostream_iterator 類別

樣板類別 ostream_iterator 描述輸出迭代器物件寫入輸出資料流，使用擷取後續項目， `operator <<`。

## <a name="syntax"></a>語法

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>參數

*Type*<br/>
要插入至輸出資料流的物件類型。

*CharType*<br/>
類型，表示 `ostream_iterator` 的字元類型。 這個引數是選擇性的預設值是**char**。

*特性*<br/>
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

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式\* `i`  =  `x`。|
|[operator++](#op_add_add)|無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。|
|[operator=](#op_eq)|指派運算子，用來實作輸出迭代器運算式\* `i`  =  `x`以寫入輸出資料流。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="char_type"></a>  ostream_iterator::char_type

類型，提供迭代器的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `CharType`的同義字。

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

## <a name="op_star"></a>  ostream_iterator::operator*

取值運算子，用來實作輸出迭代器運算式 \* *ii* = *x*。

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

針對輸出迭代器的需求，`ostream_iterator` 必須滿足僅要求運算式 \* *ii* = *t* 有效，且本身不涉及**運算子**或 `operator=`。 成員運算子在此實作中會傳回 **\*this**。

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

## <a name="op_add_add"></a>  ostream_iterator::operator++

無作用的遞增運算子，傳回 `ostream_iterator`，指向在呼叫作業之前它所定址的相同物件。

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>傳回值

`ostream_iterator` 的參考。

### <a name="remarks"></a>備註

這些成員運算子都會傳回 **\*this**。

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

## <a name="op_eq"></a>  ostream_iterator::operator=

指派運算子，用來實作 output_iterator 運算式\* `i`  =  `x`以寫入輸出資料流。

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>參數

*val*<br/>
要插入至輸出資料流的 `Type` 類型物件值。

### <a name="return-value"></a>傳回值

運算子會將*val*與物件相關聯的輸出資料流，後面接著中指定的分隔符號[ostream_iterator 建構函式](#ostream_iterator)（如果有的話），然後傳回的參考`ostream_iterator`.

### <a name="remarks"></a>備註

輸出迭代器的需求，`ostream_iterator`必須滿足僅要求運算式\* `ii`  =  `t`有效，且本身不涉及運算子或運算子 = 靠自己。 此成員運算子會傳回 `*this`。

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

## <a name="ostream_iterator"></a>  ostream_iterator::ostream_iterator

建構初始化和分隔以寫入輸出資料流的 `ostream_iterator`。

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>參數

*_Ostr*<br/>
要逐一查看之類型 [ostream_iterator::ostream_type](#ostream_type) 的輸出資料流。

*（_d)*<br/>
要插入至輸出資料流值之間的分隔符號。

### <a name="remarks"></a>備註

第一個建構函式會使用 `&_Ostr` 初始化輸出資料流指標。 分隔符號字串指標指定為空字串。

第二個建構函式會初始化輸出資料流指標`&_Ostr`和 使用分隔符號字串指標 *（_d)*。

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

## <a name="ostream_type"></a>  ostream_iterator::ostream_type

類型，提供迭代器的資料流類型。

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>備註

此類型與 [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`> 同義，這是 iostream 階層的資料流類別，定義可用於寫入的物件。

### <a name="example"></a>範例

如需如何宣告及使用 `ostream_type` 的範例，請參閱 [ostream_iterator](#ostream_iterator)。

## <a name="traits_type"></a>  ostream_iterator::traits_type

類型，提供迭代器的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Traits`的同義字。

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

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

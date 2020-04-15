---
title: istreambuf_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 80bca2160f2e60938e9d0c85557b11a273c23264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363067"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator 類別

類範本istreambuf_iterator描述一個輸入反覆運算器物件,該物件從輸入流緩衝區中提取字元元素,該緩衝區通過它存儲的對象訪問該物件,類型指標指向`basic_streambuf`\< **CharType,Traits** **Traits**>。

## <a name="syntax"></a>語法

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>參數

*字元類型*\
類型，表示 istreambuf_iterator 的字元類型。

*性狀*\
類型，表示 istreambuf_iterator 的字元類型。 這個引數是選用引數，且預設值是 `char_traits`\< *CharType>*。

## <a name="remarks"></a>備註

istreambuf_iterator 類別必須符合輸入迭代器的需求。

在建構或遞增具有非 Null 預存指標的 istreambuf_iterator 類別物件之後，物件會實際嘗試從關聯的輸入資料流中擷取和儲存 *CharType* 類型物件。 然而，擷取可能會延遲，直到物件實際上已取值或複製。 如果擷取失敗，物件是實際上會將儲存的指標取代為 null 指標，因而建立序列結尾指標。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|建構 `istreambuf_iterator`，初始化以從輸入資料流讀取字元。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，提供 `ostreambuf_iterator` 的字元類型。|
|[int_type](#int_type)|類型，提供 `istreambuf_iterator` 的整數類型。|
|[istream_type](#istream_type)|類型，提供 `istream_iterator` 的資料流類型。|
|[streambuf_type](#streambuf_type)|類型，提供 `istreambuf_iterator` 的資料流類型。|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|類型，提供 `istream_iterator` 的字元特性類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[平等](#equal)|測試兩個輸入資料流緩衝區迭代器是否相等。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_star)|取值運算子傳回資料流的下一個字元。|
|[運算子*](#op_add_add)|從輸入資料流傳回下一個字元，或在遞增之前複製物件並傳回複本。|
|[運算子>](#op_arrow)|傳回成員的值 (如果有)。|

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator:char_type

類型，提供 `ostreambuf_iterator` 的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 *CharType* 的同義字。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator:等於

測試兩個輸入資料流緩衝區迭代器是否相等。

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>參數

*對*\
要檢查其相等性的迭代器。

### <a name="return-value"></a>傳回值

如果兩個 `istreambuf_iterator` 都是或都不是資料流結尾迭代器，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

範圍由`istreambuf_iterator`到 當前位置和流端反覆運算器定義,但由於所有非流端反覆運算`equal`器在成員函數下是等效的,因此`istreambuf_iterator`無法使用 s 定義任何子範圍。 `==` 和 `!=` 運算子的語意相同。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator::int_type

類型，提供 `istreambuf_iterator` 的整數類型。

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>備註

這個類型與 `Traits::int_type`同義。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator:istream_type

類型，提供 `istreambuf_iterator` 的資料流類型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>備註

該類型是`basic_istream`\<**字元類型**的同義詞,**特徵**>。

### <a name="example"></a>範例

如需如何宣告及使用 `istream_type` 的範例，請參閱 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator:istreambuf_iterator

建構會初始化以從輸入資料流讀取字元的 istreambuf_iterator。

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>參數

*斯特布夫*\
要附加 `istreambuf_iterator` 的輸入資料流緩衝區。

*_Istr*\
要附加 `istreambuf_iterator` 的輸入資料流。

### <a name="remarks"></a>備註

第一個建構函數用*strbuf*初始化輸入流緩衝區指標。 第二個構造函數用 *_Istr*初始化輸入流緩衝區指標。 `rdbuf`,然後最終嘗試提取和存儲類型`CharType`的物件。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator::操作員*

取值運算子傳回資料流的下一個字元。

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>傳回值

資料流中的下一個字元。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator::操作員*

從輸入資料流傳回下一個字元，或在遞增之前複製物件並傳回複本。

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>傳回值

`istreambuf_iterator` 或對 `istreambuf_iterator` 的參考。

### <a name="remarks"></a>備註

第一個運算符最終嘗試從關聯的輸入流中提取和存儲`CharType`類型的物件。 第二個運算子會複製物件、遞增物件，然後傳回複本。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator:操作員-&gt;

傳回成員的值 (如果有)。

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>傳回值

運算子**&\*傳回\*此**。

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator:streambuf_type

一種類型，提供 istreambuf_iterator 的資料流類型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>備註

該類型是`basic_streambuf`\<**字元類型**的同義詞,**特徵**>。

### <a name="example"></a>範例

如需如何宣告及使用 `istreambuf_type` 的範例，請參閱 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator:traits_type

類型，提供 `istream_iterator` 的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Traits* 同義。

### <a name="example"></a>範例

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>另請參閱

[反覆發化器結構](../standard-library/iterator-struct.md)\
[\<反覆運算器>](../standard-library/iterator.md)\
[C++標準庫中的線程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++標準函式庫參考](../standard-library/cpp-standard-library-reference.md)

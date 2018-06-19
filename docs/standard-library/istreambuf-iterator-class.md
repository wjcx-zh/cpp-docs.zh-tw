---
title: istreambuf_iterator 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
dev_langs:
- C++
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 810f565d85a923379a25f49c6fe1c7d7cc4efbc5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859276"
---
# <a name="istreambufiterator-class"></a>istreambuf_iterator 類別

範本類別 istreambuf_iterator 描述一個輸入迭代器物件，此物件會從輸入資料流緩衝區擷取字元元素，其中會透過它所儲存的物件 (屬於 `basic_streambuf`\< **CharType**, **Traits** 的 pointer 類型) 來存取該緩衝區。

## <a name="syntax"></a>語法

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>參數

`CharType` 表示 istreambuf_iterator 的字元類型的型別。

`Traits` 表示 istreambuf_iterator 的字元類型的型別。 這個引數是選用引數，且預設值是 `char_traits`\< *CharType>*。

## <a name="remarks"></a>備註

istreambuf_iterator 類別必須符合輸入迭代器的需求。

在建構或遞增具有非 Null 預存指標的 istreambuf_iterator 類別物件之後，物件會實際嘗試從關聯的輸入資料流中擷取和儲存 **CharType** 類型物件。 然而，擷取可能會延遲，直到物件實際上已取值或複製。 如果擷取失敗，物件是實際上會將儲存的指標取代為 null 指標，因而建立序列結尾指標。

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

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[equal](#equal)|測試兩個輸入資料流緩衝區迭代器是否相等。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子傳回資料流的下一個字元。|
|[operator++](#op_add_add)|從輸入資料流傳回下一個字元，或在遞增之前複製物件並傳回複本。|
|[operator->](#op_arrow)|傳回成員的值 (如果有)。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="char_type"></a>  istreambuf_iterator::char_type

類型，提供 `ostreambuf_iterator` 的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數 **CharType** 同義。

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

## <a name="equal"></a>  istreambuf_iterator::equal

測試兩個輸入資料流緩衝區迭代器是否相等。

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>參數

`right` 這是要檢查相等的迭代器。

### <a name="return-value"></a>傳回值

如果兩個 `istreambuf_iterator` 都是或都不是資料流結尾迭代器，便會傳回 **true**；否則會傳回 **false**。

### <a name="remarks"></a>備註

範圍是由指向目前位置的 `istreambuf_iterator` 和資料流結尾迭代器所定義，但由於所有非資料流結尾迭代器在 **equal** 成員函式下都相等，因此無法使用 `istreambuf_iterator` 來定義任何子範圍。 `==` 和 `!=` 運算子的語意相同。

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

## <a name="int_type"></a>  istreambuf_iterator::int_type

類型，提供 `istreambuf_iterator` 的整數類型。

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>備註

此類型與 **Traits::int_type** 同義。

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
\* Output:
The inttype1 = 100.
*\
```

## <a name="istream_type"></a>  istreambuf_iterator::istream_type

類型，提供 `istreambuf_iterator` 的資料流類型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>備註

此類型與 `basic_istream`\< **CharType**, **Traits**> 同義。

### <a name="example"></a>範例

如需如何宣告及使用 `istream_type` 的範例，請參閱 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="istreambuf_iterator"></a>  istreambuf_iterator::istreambuf_iterator

建構會初始化以從輸入資料流讀取字元的 istreambuf_iterator。

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>參數

`strbuf` 輸入資料流緩衝區`istreambuf_iterator`正在附加。

`_Istr` 輸入資料流的`istreambuf_iterator`正在附加。

### <a name="remarks"></a>備註

第一個建構函式會使用 `strbuf` 將輸入資料流緩衝區指標初始化。 第二個建構函式會使用 `_Istr` 將輸入資料流緩衝區指標初始化。 最後，`rdbuf` 會接著嘗試擷取並儲存 **CharType** 類型的物件。

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

## <a name="op_star"></a>  istreambuf_iterator::operator*

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

## <a name="op_add_add"></a>  istreambuf_iterator::operator++

從輸入資料流傳回下一個字元，或在遞增之前複製物件並傳回複本。

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>傳回值

`istreambuf_iterator` 或對 `istreambuf_iterator` 的參考。

### <a name="remarks"></a>備註

第一個運算子最後會嘗試從關聯的輸入資料流中擷取並儲存 **CharType** 類型的物件。 第二個運算子會複製物件、遞增物件，然後傳回複本。

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

## <a name="op_arrow"></a>  istreambuf_iterator::operator-&gt;

傳回成員的值 (如果有)。

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>傳回值

運算子會傳回 **&\*\*this**。

## <a name="streambuf_type"></a>  istreambuf_iterator::streambuf_type

一種類型，提供 istreambuf_iterator 的資料流類型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>備註

此類型與 `basic_streambuf`\< **CharType**, **Traits**> 同義。

### <a name="example"></a>範例

如需如何宣告及使用 **istreambuf_type** 的範例，請參閱 [istreambuf_iterator](#istreambuf_iterator)。

## <a name="traits_type"></a>  istreambuf_iterator::traits_type

類型，提供 `istream_iterator` 的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 **Traits** 同義。

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

[iterator 結構](../standard-library/iterator-struct.md)<br/>
[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

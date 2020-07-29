---
title: ostreambuf_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: e4e21bd0c1323afdc2c81a0e581c3557b8040193
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87202437"
---
# <a name="ostreambuf_iterator-class"></a>ostreambuf_iterator 類別

類別樣板 ostreambuf_iterator 描述輸出反覆運算器物件，它會使用>>的抽取**運算子**，將後續的字元元素寫入至輸出資料流程。 `ostreambuf_iterator` 與 [ostream_iterator 類別](../standard-library/ostream-iterator-class.md)的不同處在於字元 (而非泛型類型) 做為要插入至輸出資料流的物件類型。

## <a name="syntax"></a>語法

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>參數

*CharType*\
類型，表示 ostreambuf_iterator 的字元類型。 這個引數是選擇性的，而且預設值是 **`char`** 。

*共同*\
類型，表示 ostreambuf_iterator 的字元類型。 這個引數是選擇性的，而且預設值是 `char_traits` \< *CharType> . *

## <a name="remarks"></a>備註

ostreambuf_iterator 類別必須符合輸出迭代器的需求。 使用 `ostreambuf_iterator`，演算法可以直接寫入輸出資料流。 此類別提供低階資料流迭代器，允許存取字元格式的原始 (未格式化) I/O 資料流，也能夠略過與進階資料流迭代器相關聯的緩衝和字元轉譯。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|建構 `ostreambuf_iterator`，初始化以將字元寫入輸出資料流中。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，提供 `ostreambuf_iterator` 的字元類型。|
|[ostream_type](#ostreambuf_iterator_ostream_type)|類型，提供 `ostream_iterator` 的資料流類型。|
|[streambuf_type](#streambuf_type)|類型，提供 `ostreambuf_iterator` 的資料流類型。|
|[traits_type](#traits_type)|類型，提供 `ostream_iterator` 的字元特性類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[發生](#failed)|測試插入至輸出資料流緩衝區是否失敗。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[操作](#op_star)|取值運算子，用來執行輸出反覆運算器運算式 \* `i`  =  `x` 。|
|[operator + +](#op_add_add)|無作用的遞增運算子，傳回 `ostreambuf_iterator`，指向在呼叫作業之前它所定址的相同物件。|
|[operator =](#op_eq)|此運算子會將字元插入至相關聯的資料流緩衝區。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator：： char_type

類型，提供 `ostreambuf_iterator` 的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator：： failed

測試插入至輸出資料流緩衝區是否失敗。

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>傳回值

**`true`** 如果沒有插入輸出資料流程緩衝區的先前失敗，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

**`true`** 如果任何先前使用的成員，成員函 `operator=` 式會傳回**subf**_-> 的呼叫會 `sputc` 傳回**eof**。

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator：： operator\*

用來執行輸出反覆運算器運算式 \* *i*  =  *x*的非功能性取值運算子。

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>傳回值

ostreambuf 迭代器物件。

### <a name="remarks"></a>備註

這個運算子只會在輸出反覆運算器運算式 \* *i*  =  *x*中運作，以將字元輸出到資料流程緩衝區。 套用至 ostreambuf iterator，它會傳回反覆運算器;** \* iter**會傳回**iter**，

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator：： operator + +

無作用的遞增運算子，傳回 ostream 迭代器，指向在呼叫作業之前它所定址的相同字元。

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>傳回值

原本所定址之字元的參考，或可轉換成的實作為定義物件 `ostreambuf_iterator` \< **CharType**, **Traits**> 。

### <a name="remarks"></a>備註

運算子可用來執行輸出反覆運算器運算式 \* *i*  =  *x*。

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator：： operator =

此運算子會將字元插入至相關聯的資料流緩衝區。

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>參數

*_Char*\
要插入至資料流緩衝區的字元。

### <a name="return-value"></a>傳回值

插入至資料流緩衝區的字元參考。

### <a name="remarks"></a>備註

指派運算子，用來執行輸出反覆運算器運算式 \* *i*  =  *x*以寫入輸出資料流程。

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator：： ostreambuf_iterator

建構 `ostreambuf_iterator`，初始化以將字元寫入輸出資料流中。

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>參數

*strbuf*\
用於初始化輸出資料流緩衝區指標的輸出 streambuf 物件。

*Ostr*\
用於初始化輸出資料流緩衝區指標的輸出資料流物件。

### <a name="remarks"></a>備註

第一個函式會使用*strbuf*來初始化輸出資料流程緩衝區指標。

第二個建構函式會使用 `Ostr` 初始化輸出資料流緩衝區指標。 `rdbuf`. 儲存的指標不能是 null 指標。

### <a name="example"></a>範例

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator：： ostream_type

類型，提供 `ostream_iterator` 的資料流類型。

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>備註

此類型是的同義字`basicOstream`\< **CharType**, **Traits**>

### <a name="example"></a>範例

如需如何宣告及使用 `ostream_type` 的範例，請參閱 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator：： streambuf_type

類型，提供 `ostreambuf_iterator` 的資料流類型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>備註

此類型與同義 `basic_streambuf` \< **CharType**, **Traits**> ，這是在特製化 `streambuf` 為字元類型時，會變成的 i/o 緩衝區資料流程類別 **`char`** 。

### <a name="example"></a>範例

如需如何宣告及使用 `streambuf_type` 的範例，請參閱 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator：： traits_type

類型，提供 `ostream_iterator` 的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Traits` 的同義字。

### <a name="example"></a>範例

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>另請參閱

[\<iterator>](../standard-library/iterator.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

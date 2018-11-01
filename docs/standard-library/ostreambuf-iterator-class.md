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
ms.openlocfilehash: 5114a658cfde965556f4663d2ba92c9ba4d1eaeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543363"
---
# <a name="ostreambufiterator-class"></a>ostreambuf_iterator 類別

樣板類別 ostreambuf_iterator 描述輸出迭代器物件，這個物件使用擷取 **operator>>** 在輸出資料流中寫入後續字元項目。 `ostreambuf_iterator` 與 [ostream_iterator 類別](../standard-library/ostream-iterator-class.md)的不同處在於字元 (而非泛型類型) 做為要插入至輸出資料流的物件類型。

## <a name="syntax"></a>語法

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>參數

*CharType*<br/>
類型，表示 ostreambuf_iterator 的字元類型。 這個引數是選擇性的預設值是**char**。

*特性*<br/>
類型，表示 ostreambuf_iterator 的字元類型。 這個引數是選用引數，且預設值是 `char_traits`\< *CharType>*。

## <a name="remarks"></a>備註

ostreambuf_iterator 類別必須符合輸出迭代器的需求。 使用 `ostreambuf_iterator`，演算法可以直接寫入輸出資料流。 此類別提供低階資料流迭代器，允許存取字元格式的原始 (未格式化) I/O 資料流，也能夠略過與進階資料流迭代器相關聯的緩衝和字元轉譯。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|建構 `ostreambuf_iterator`，初始化以將字元寫入輸出資料流中。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，提供 `ostreambuf_iterator` 的字元類型。|
|[ostream_type](#ostreambuf_iterator_ostream_type)|類型，提供 `ostream_iterator` 的資料流類型。|
|[streambuf_type](#streambuf_type)|類型，提供 `ostreambuf_iterator` 的資料流類型。|
|[traits_type](#traits_type)|類型，提供 `ostream_iterator` 的字元特性類型。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[failed](#failed)|測試插入至輸出資料流緩衝區是否失敗。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子，用來實作輸出迭代器運算式\* `i`  =  `x`。|
|[operator++](#op_add_add)|無作用的遞增運算子，傳回 `ostreambuf_iterator`，指向在呼叫作業之前它所定址的相同物件。|
|[operator=](#op_eq)|此運算子會將字元插入至相關聯的資料流緩衝區。|

## <a name="requirements"></a>需求

**標頭：**\<iterator>

**命名空間：** std

## <a name="char_type"></a>  ostreambuf_iterator::char_type

類型，提供 `ostreambuf_iterator` 的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `CharType`的同義字。

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

## <a name="failed"></a>  ostreambuf_iterator::failed

測試插入至輸出資料流緩衝區是否失敗。

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>傳回值

如果之前插入至輸出資料流緩衝區沒有失敗，則為 **true**；否則為 **false**。

### <a name="remarks"></a>備註

如果任何之前使用成員 `operator=` 呼叫 **subf**_-> `sputc` 傳回了 **eof**，成員函式會傳回 **true**。

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

## <a name="op_star"></a>  ostreambuf_iterator:: operator\*

無作用的取值運算子，用來實作輸出迭代器運算式 \* *i* = *x*。

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>傳回值

ostreambuf 迭代器物件。

### <a name="remarks"></a>備註

此運算子只能在輸出迭代器運算式 \* *i* = *x* 中運作，將字元輸出到資料流緩衝區。 若套用至 ostreambuf 迭代器，它會傳回迭代器；**\*iter** 則傳回 **iter**。

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

## <a name="op_add_add"></a>  ostreambuf_iterator::operator++

無作用的遞增運算子，傳回 ostream 迭代器，指向在呼叫作業之前它所定址的相同字元。

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>傳回值

針對原先定址的字元，或是轉換為 `ostreambuf_iterator`\< **CharType**, **Traits**> 之實作定義物件的參考。

### <a name="remarks"></a>備註

此運算子用來實作輸出迭代器運算式 \* *i* = *x*。

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

## <a name="op_eq"></a>  ostreambuf_iterator::operator=

此運算子會將字元插入至相關聯的資料流緩衝區。

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>參數

*_Char*<br/>
要插入至資料流緩衝區的字元。

### <a name="return-value"></a>傳回值

插入至資料流緩衝區的字元參考。

### <a name="remarks"></a>備註

指派運算子，用來實作輸出迭代器運算式 \* *i* = *x*，以寫入輸出資料流。

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

## <a name="ostreambuf_iterator_ostreambuf_iterator"></a>  ostreambuf_iterator::ostreambuf_iterator

建構 `ostreambuf_iterator`，初始化以將字元寫入輸出資料流中。

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>參數

*strbuf*<br/>
用於初始化輸出資料流緩衝區指標的輸出 streambuf 物件。

*Ostr*<br/>
用於初始化輸出資料流緩衝區指標的輸出資料流物件。

### <a name="remarks"></a>備註

第一個建構函式會初始化輸出資料流緩衝區指標*strbuf*。

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

## <a name="ostreambuf_iterator_ostream_type"></a>  ostreambuf_iterator::ostream_type

類型，提供 `ostream_iterator` 的資料流類型。

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>備註

這個類型與 `basicOstream`\< **CharType**, **Traits**> 同義

### <a name="example"></a>範例

如需如何宣告及使用 `ostream_type` 的範例，請參閱 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。

## <a name="streambuf_type"></a>  ostreambuf_iterator::streambuf_type

類型，提供 `ostreambuf_iterator` 的資料流類型。

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>備註

類型是同義字`basic_streambuf` \< **CharType**，**特性**>，成為 I/O 緩衝區資料流類別`streambuf`時特製化為字元類型**char**。

### <a name="example"></a>範例

如需如何宣告及使用 `streambuf_type` 的範例，請參閱 [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)。

## <a name="traits_type"></a>  ostreambuf_iterator::traits_type

類型，提供 `ostream_iterator` 的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Traits`的同義字。

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

[\<iterator>](../standard-library/iterator.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

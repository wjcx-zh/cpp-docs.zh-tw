---
title: istream_iterator 類別
ms.date: 11/04/2016
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
ms.openlocfilehash: 941d625e388edc75dfe25a2de0e609c6d955ff19
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447748"
---
# <a name="istreamiterator-class"></a>istream_iterator 類別

描述輸入迭代器物件。 它會從輸入資料流擷取 `Type` 類別的物件，其中會透過它所儲存的物件 (屬於 `basic_istream`< `CharType`, `Traits` 的 `pointer` 類型) 來存取該資料流。

## <a name="syntax"></a>語法

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>參數

*型*\
要輸入資料流擷取的物件類型。

*CharType*\
類型，表示 `istream_iterator` 的字元類型。 這個引數是選擇性的, 而且預設值為**char**。

*共同*\
類型，表示 `istream_iterator` 的字元類型。 這個引數是選用引數，且預設值是 `char_traits`< `CharType`>。

*長途電話*\
帶正負號的整數類資料類型，表示 `istream_iterator` 的差異類型。 這個引數是選擇性的，而且預設值是 `ptrdiff_t`。

在建構或遞增具有非 null 儲存指標的 istream_iterator 類別物件之後，物件會嘗試從關聯的輸入資料流擷取和儲存 `Type` 類型物件。 如果擷取失敗，物件是實際上會將儲存的指標取代為 null 指標，因而建立序列結尾指標。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[istream_iterator](#istream_iterator)|建構資料流結尾迭代器做為預設 `istream_iterator`，或建構 `istream_iterator`，初始化為從中讀取的迭代器資料流類型。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，提供 `istream_iterator` 的字元類型。|
|[istream_type](#istream_type)|類型，提供 `istream_iterator` 的資料流類型。|
|[traits_type](#traits_type)|類型，提供 `istream_iterator` 的字元特性類型。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator*](#op_star)|取值運算子傳回 `Type` 類型 (由 `istream_iterator` 定址) 的儲存物件。|
|[operator->](#op_arrow)|傳回成員的值 (如果有)。|
|[operator++](#op_add_add)|從輸入資料流擷取遞增物件，或在遞增之前複製物件並傳回複本。|

## <a name="requirements"></a>需求

**標頭：** \<iterator>

**命名空間：** std

## <a name="char_type"></a>  istream_iterator::char_type

類型，提供 `istream_iterator` 的字元類型。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Chartype`的同義字。

### <a name="example"></a>範例

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iterator"></a>  istream_iterator::istream_iterator

建構資料流結尾迭代器做為預設 `istream_iterator`，或建構 `istream_iterator`，初始化為從中讀取的迭代器資料流類型。

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>參數

*_Istr*\
要讀取的輸入資料流，用來將 `istream_iterator` 初始化。

### <a name="remarks"></a>備註

第一個建構函式會使用 Null 指標將輸入資料流指標初始化，並建立資料流結尾迭代器。 第二個函式會使用 *& _Istr*將輸入資料流程指標初始化, 然後嘗試解壓縮並儲存類型`Type`的物件。

資料流結尾迭代器可以用來測試 `istream_iterator` 是否已到達資料流的結尾。

### <a name="example"></a>範例

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_type"></a>  istream_iterator::istream_type

類型，提供 `istream_iterator` 的資料流類型。

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>備註

此類型與 `basic_istream`\< **CharType**, **Traits**> 同義。

### <a name="example"></a>範例

如需如何宣告及使用 `istream_type` 的範例，請參閱 [istream_iterator](#istream_iterator)。

## <a name="op_star"></a>  istream_iterator::operator*

取值運算子傳回 `Type` 類型 (由 `istream_iterator` 定址) 的儲存物件。

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>傳回值

類型`Type`的預存物件。

### <a name="example"></a>範例

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_arrow"></a>  istream_iterator::operator-&gt;

傳回成員的值 (如果有)。

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>傳回值

成員的值 (如果有)。

### <a name="remarks"></a>備註

`i->m`相當於`(*i).m`

第一個運算子會傳回 `&*this`。

### <a name="example"></a>範例

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="op_add_add"></a>  istream_iterator::operator++

從輸入資料流擷取遞增物件，或在遞增之前複製物件並傳回複本。

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>傳回值

第一個成員運算子會傳回從輸入資料流程解壓縮之類型`Type`的遞增物件參考, 而第二個成員函式會傳回物件的複本。

### <a name="example"></a>範例

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="traits_type"></a>  istream_iterator::traits_type

類型，提供 `istream_iterator` 的字元特性類型。

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 *Traits* 同義。

### <a name="example"></a>範例

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>另請參閱

[input_iterator_tag 結構](../standard-library/input-iterator-tag-struct.md)\
[iterator 結構](../standard-library/iterator-struct.md)\
[\<iterator>](../standard-library/iterator.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

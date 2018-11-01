---
title: '&lt;bitset&gt; 運算子'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: c51bc5ecf2bc3a74b25a06320f0ca8fd64749f5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531140"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 運算子

||||
|-|-|-|
|[operator&amp;](#op_amp)|[operator&gt;&gt;](#op_gt_gt)|[operator&lt;&lt;](#op_lt_lt)|
|[operator^](#op_xor)|[operator|](#op_or)|

## <a name="op_amp"></a> operator&amp;

在兩個 bitset 之間執行位元 `AND`。

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `AND` 結合。

*right*<br/>
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `AND` 結合。

### <a name="return-value"></a>傳回值

Bitset，其項目是執行的結果`AND`的對應項目上的作業*左*並*右*。

### <a name="example"></a>範例

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a> operator&lt;&lt;

將位元序列的文字表示插入輸出資料流。

```

template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>參數

*right*<br/>
要當做字串插入輸出資料流之 **bitset\<N>** 類型的物件。

### <a name="return-value"></a>傳回值

位元序列中的文字表示法`ostr`。

### <a name="remarks"></a>備註

範本函式多載`operator<<`，允許 bitset，寫出，而不先將它轉換成字串。 樣板函式有效地執行：

**ostr** << _ *Right*. [to_string](bitset-class.md) < **CharType**, **Traits**, **allocator**\< **CharType**> > ( )

### <a name="example"></a>範例

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a> operator&gt;&gt;

將位元字元的字串讀入 bitset。

```

template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>&
_Istr,
    bitset<N>&
    right);
```

### <a name="parameters"></a>參數

*_Istr*<br/>
在輸入資料流中輸入以插入 bitset 的字串。

*right*<br/>
要從輸入資料流接收位元的 bitset。

### <a name="return-value"></a>傳回值

範本函式會傳回字串 *_Istr*。

### <a name="remarks"></a>備註

範本函式多載`operator>>`來儲存在 bitset _*右*值 bitset (`str`)，其中`str`是類型的物件[basic_string](basic-string-class.md)  < **Chartype>**，**特性**，**配置器**\< **CharType**>>  **&** 取自 *_Istr*。

此範本函式擷取項目 *_Istr*並將其插入 bitset，直到：

- 已從輸入資料流中擷取所有位元元素並將其儲存在 bitset 中。

- 已使用輸入資料流中的位元填滿 bitset。

- 遇到不是 0 或 1 的輸入元素。

### <a name="example"></a>範例

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a>  operator^

在兩個 bitset 之間執行位元 `EXCLUSIVE-OR`。

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。

*right*<br/>
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。

### <a name="return-value"></a>傳回值

Bitset，其項目是執行的結果`EXCLUSIVE-OR`的對應項目上的作業*左*並*右*。

### <a name="example"></a>範例

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a>  運算子 |

在兩個 bitset 之間執行位元 `OR`。

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*left*<br/>
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `OR` 結合。

*right*<br/>
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `OR` 結合。

### <a name="return-value"></a>傳回值

Bitset，其項目是執行的結果`OR`的對應項目上的作業*左*並*右*。

### <a name="example"></a>範例

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```

## <a name="see-also"></a>另請參閱

[\<bitset>](../standard-library/bitset.md)<br/>

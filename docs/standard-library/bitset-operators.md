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
ms.openlocfilehash: 23c6abffe7e433a0550c45502a12e9adaf652a33
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257984"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset&gt; 運算子

## <a name="op_amp"></a> 運算子&amp;

在兩個 bitset 之間執行位元 `AND`。

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*左方*\
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `AND` 結合。

*right*\
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `AND` 結合。

### <a name="return-value"></a>傳回值

Bitset，其元素是對*left*和*right*的對應元素執行 `AND` 運算的結果。

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

## <a name="op_lt_lt"></a>運算子&lt;&lt;

將位元序列的文字表示插入輸出資料流。

```cpp
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>參數

*right*\
要當做字串插入輸出資料流之 **bitset\<N>** 類型的物件。

### <a name="return-value"></a>傳回值

`ostr`中位序列的文字表示。

### <a name="remarks"></a>備註

範本函式會 `operator<<`多載，允許寫出 bitset，而不先將它轉換成字串。 樣板函式有效地執行：

`ostr << right.`[to_string](bitset-class.md)`<CharType, Traits, allocator<CharType>>()`

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

## <a name="op_gt_gt"></a>運算子&gt;&gt;

將位元字元的字串讀入 bitset。

```cpp
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>& i_str,
    bitset<N>& right);
```

### <a name="parameters"></a>參數

*i_str*\
在輸入資料流中輸入以插入 bitset 的字串。

*right*\
要從輸入資料流接收位元的 bitset。

### <a name="return-value"></a>傳回值

此範本函式會傳回*i_str*的字串。

### <a name="remarks"></a>備註

樣板函式會多載 `operator>>` 以將值 `bitset(str)`儲存在 bitset*右側*，其中 `str` 是[basic_string](basic-string-class.md)`< CharType, Traits, allocator< CharType > >&` 從*i_str*中解壓縮的類型的物件。

此範本函式會從*i_str*解壓縮專案，並將其插入至 bitset 中，直到：

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

## <a name="op_xor"></a>運算子 ^

在兩個 bitset 之間執行位元 `EXCLUSIVE-OR`。

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*左方*\
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。

*right*\
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `EXCLUSIVE-OR` 結合。

### <a name="return-value"></a>傳回值

Bitset，其元素是對*left*和*right*的對應元素執行 `EXCLUSIVE-OR` 運算的結果。

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

## <a name="op_or"></a>操作&#124;

在兩個 bitset 之間執行位元 `OR`。

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>參數

*左方*\
兩個 bitset 的第一個 bitset，其相關元素會使用位元 `OR` 結合。

*right*\
兩個 valarray 的第二個 valarray，其相關元素會使用位元 `OR` 結合。

### <a name="return-value"></a>傳回值

Bitset，其元素是對*left*和*right*的對應元素執行 `OR` 運算的結果。

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

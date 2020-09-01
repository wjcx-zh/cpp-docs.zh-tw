---
title: '&lt;位 &gt; 函數'
description: 存取、操作及處理個別位和位順序的函式
ms.date: 08/28/2020
f1_keywords:
- bit/std::bit_cast
- bit/std::has_single_bit
- bit/std::bit_ceil
- bit/std::bit_floor
- bit/std::bit_width
- bit/std::rotl
- bit/std::rotr
- bit/std::countl_zero
- bit/std::countl_one
- bit/std::countr_zero
- bit/std::countr_one
- bit/std::popcount
helpviewer_keywords:
- std::bit [C++], bit_cast
- std::bit [C++], has_single_bit
- std::bit [C++], bit_ceil
- std::bit [C++], bit_floor
- std::bit [C++], bit_width
- std::bit [C++], rotl
- std::bit [C++], rotr
- std::bit [C++], countl_zero
- std::bit [C++], countl_one
- std::bit [C++], countr_zero
- std::bit [C++], countr_one
- std::bit [C++], popcount
ms.openlocfilehash: f06e181a4fe6683adb0cc63c016cbd879f2fc574
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281805"
---
# <a name="ltbitgt-functions"></a>&lt;位 &gt; 函數

\<bit>標頭包含下列非成員範本函數：

| **非成員函式** | **描述** |
|--------|---------|
|[bit_cast](#bit_cast) | 將物件表示從某個類型重新解譯至另一個類型。 |
|[bit_ceil](#bit_ceil) | 找出兩個大於或等於某個值的最小乘冪。 |
|[bit_floor](#bit_floor) | 找出兩個不大於某個值的最大乘冪。 |
|[bit_width](#bit_width) | 找出表示值所需的最小位數。 |
|[countl_zero](#countl_zero) | 從最重要的位開始計算設定為零的連續位數。 |
|[countl_one](#countl_one) | 從最重要的位開始計算設定為一個的連續位數。 |
|[countr_zero](#countr_zero) | 從最不重要的位算起，計算設定為零的連續位數。 |
|[countr_one](#countl_one) | 從最不重要的位算起，計算設定為1的連續位數。 |
|[has_single_bit](#has_single_bit) | 檢查某個值是否只有一個位設定為一個。 這和測試值是否為2的乘冪一樣。 |
|[popcount](#popcount) | 計算設定為1的位數目。 |
|[rotl](#rotl) | 計算位左旋轉的結果。 |
|[rotr](#rotr) | 計算位右旋轉的結果。 |

## <a name="bit_cast"></a>`bit_cast`

從類型的物件將位模式複製 `From` 到類型的新物件 `To` 。

```cpp
template <class To, class From>
[[nodiscard]] constexpr To bit_cast(const From& from) noexcept;
```

### <a name="parameters"></a>參數

*自*\
輸出的型別。

*從*\
所要轉換值的類型。

*從*\
要進行轉換的值。

### <a name="return-value"></a>傳回值

`To` 類型的物件。

結果中的每個位都符合中的對應位 `from` ，除非在中有填補位 `To` ，在這種情況下，結果中的位不會指定。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <iostream>

int main()
{
    float f = std::numeric_limits<float>::infinity();
    int i = std::bit_cast<int>(f);
    std::cout << "float f = " << std::hex << f
              << "\nstd::bit_cat<int>(f) = " << std::hex << i << '\n';
    return 0;
}
```

```Output
float f = inf
std::bit_cat<int>(f) = 7f800000
```

### <a name="remarks"></a>備註

低層級程式碼通常需要將一個類型的物件解讀為另一個類型。 重新解譯物件與原始物件具有相同的位標記法，但它是不同的類型。

不使用 `reinterpret_cast` 或 `memcpy()` ， `bit_cast()` 是進行這些轉換的較佳方式。 更好的原因是：
- `bit_cast()` 是 `constexpr`
- `bit_cast()` 需要完整可複製和相同大小的類型。 這可防止您可能遇到的潛在問題， `reinterpret_cast` 並 `memcpy` 因為它們可以用來不慎且不正確地轉換非完整可複製類型。 此外，也可以 `memcpy()` 用來不慎複製大小不相同的類型。 例如，double (8 個位元組) 為不帶正負號的 int (4 個位元組) 或其他方面。

如果有下列情況，這個多載只會參與多載解析：
-  `sizeof(To) == sizeof(From)`
- `To` 和 `From` 都 [is_trivially_copyable](https://docs.microsoft.com/cpp/standard-library/is-trivially-copyable-class?view=vs-2019`)。

只有在、和其子類別的類型為時，這個函式範本才是 `constexpr` `To` `From` ：
- 不是等位或指標類型
- 不是成員類型的指標
- 非 volatile 限定
- 沒有屬於參考型別的非靜態資料成員

## <a name="bit_ceil"></a>`bit_ceil`

找出兩個大於或等於某個值的最小乘冪。 例如，指定的會傳回 `3` `4` 。

```cpp
template<class T>
[[nodiscard]] constexpr T bit_ceil(T value);
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

 兩個大於或等於的最小乘冪 `value` 。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_ceil() takes an unsigned integer type
    {
        auto nextClosestPowerOf2 = std::bit_ceil(i);
        std::cout << "\nbit_ceil(0b" << std::bitset<4>(i) << ") = "
                  << "0b" << std::bitset<4>(nextClosestPowerOf2);
    }
    return 0;
}
```

```Output
bit_ceil(0b0000) = 0b0001
bit_ceil(0b0001) = 0b0001
bit_ceil(0b0010) = 0b0010
bit_ceil(0b0011) = 0b0100
bit_ceil(0b0100) = 0b0100
bit_ceil(0b0101) = 0b1000
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="bit_floor"></a>`bit_floor`

找出兩個不大於某個值的最大乘冪。 例如，指定的會傳回 `5` `4` 。

```cpp
template< class T >
[[nodiscard]] constexpr T bit_floor(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

兩個不大於的最大乘冪 `value` 。
如果 `value` 是零，則會傳回零。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_floor() takes an unsigned integer type
    {
        auto previousPowerOf2 = std::bit_floor(i);
        std::cout << "\nbit_floor(0b" << std::bitset<4>(i) << ") = 0b"
                  << std::bitset<4>(previousPowerOf2);
    }
    return 0;
}
```

```Output
bit_floor(0b0000) = 0b0000
bit_floor(0b0001) = 0b0001
bit_floor(0b0010) = 0b0010
bit_floor(0b0011) = 0b0010
bit_floor(0b0100) = 0b0100
bit_floor(0b0101) = 0b0100
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="bit_width"></a>`bit_width`

找出表示值所需的最小位數。

例如，假設有5個 (0b101) ，則會傳回3，因為它會使用3個二進位位來表示5的值。

```cpp
template<class T>
[[nodiscard]] constexpr T bit_width(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

表示所需的位數 `value` 。
如果 `value` 是零，則會傳回零。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <iostream>

int main()
{
    for (unsigned i=0u; i <= 8u; ++i)
    {
        std::cout << "\nbit_width(" << i << ") = "
                  << std::bit_width(i);
    }
    return 0;
}
```

```Output
bit_width(0) = 0
bit_width(1) = 1
bit_width(2) = 2
bit_width(3) = 2
bit_width(4) = 3
bit_width(5) = 3
bit_width(6) = 3
bit_width(7) = 3
bit_width(8) = 4
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="countl_zero"></a>`countl_zero`

從最重要的位開始計算設定為零的連續位數。

```cpp
template<class T>
[[nodiscard]] constexpr int countl_zero(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

連續零位數的數目，從最重要的位開始。
如果 `value` 是零，則為類型中的位數目 `value` 。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountl_zero(0b" << std::bitset<8>(result) << ") = " << std::countl_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countl_zero(0b00000000) = 8
countl_zero(0b00000001) = 7
countl_zero(0b00000010) = 6
countl_zero(0b00000100) = 5
countl_zero(0b00001000) = 4
countl_zero(0b00010000) = 3
countl_zero(0b00100000) = 2
countl_zero(0b01000000) = 1
countl_zero(0b10000000) = 0
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="countl_one"></a>`countl_one`

從最重要的位開始計算設定為一個的連續位數。

```cpp
template<class T>
[[nodiscard]] constexpr int countl_one(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

從最重要的位開始，設定為1的連續位數。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (unsigned char bit = 128; bit > 0; bit /= 2)
    {
        value |= bit;
        std::cout << "\ncountl_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countl_one(value);
    }
    return 0;
}
```

```Output
countl_one(0b10000000) = 1
countl_one(0b11000000) = 2
countl_one(0b11100000) = 3
countl_one(0b11110000) = 4
countl_one(0b11111000) = 5
countl_one(0b11111100) = 6
countl_one(0b11111110) = 7
countl_one(0b11111111) = 8
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="countr_zero"></a>`countr_zero`

從最不重要的位算起，計算設定為零的連續位數。

```cpp
template<class T>
[[nodiscard]] constexpr int countr_zero(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

連續零位數的數目，從最不重要的位開始。
如果 `value` 是零，則為類型中的位數目 `value` 。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountr_zero(0b" << std::bitset<8>(result) << ") = "
                  << std::countr_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countr_zero(0b00000000) = 8
countr_zero(0b00000001) = 0
countr_zero(0b00000010) = 1
countr_zero(0b00000100) = 2
countr_zero(0b00001000) = 3
countr_zero(0b00010000) = 4
countr_zero(0b00100000) = 5
countr_zero(0b01000000) = 6
countr_zero(0b10000000) = 7
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="countr_one"></a>`countr_one`

從最不重要的位算起，計算設定為1的連續位數。

```cpp
template<class T>
[[nodiscard]] constexpr int countr_one(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

從最不重要的位開始，設定為1的連續位數。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (int bit = 1; bit <= 128; bit *= 2)
    {
        value |= bit;
        std::cout << "\ncountr_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countr_one(value);
    }
    return 0;
}
```

```Output
countr_one(0b00000001) = 1
countr_one(0b00000011) = 2
countr_one(0b00000111) = 3
countr_one(0b00001111) = 4
countr_one(0b00011111) = 5
countr_one(0b00111111) = 6
countr_one(0b01111111) = 7
countr_one(0b11111111) = 8
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="has_single_bit"></a>`has_single_bit`

檢查某個值是否只有一個位設定。這和測試值是否為2的乘冪一樣。
 
```cpp
template <class T>
[[nodiscard]] constexpr bool has_single_bit(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

`true` 如果 `value` 只有一個位集，也就 `value` 是兩個的乘冪。 否則為 `false`。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>
#include <iomanip>

int main()
{
    for (auto i = 0u; i < 10u; ++i)
    {
        std::cout << "has_single_bit(0b" << std::bitset<4>(i) << ") = "
                  << std::boolalpha << std::has_single_bit(i) << '\n';
    }
    return 0;
}
```

```Output
has_single_bit(0b0000) = false
has_single_bit(0b0001) = true
has_single_bit(0b0010) = true
has_single_bit(0b0011) = false
has_single_bit(0b0100) = true
has_single_bit(0b0101) = false
has_single_bit(0b0110) = false
has_single_bit(0b0111) = false
has_single_bit(0b1000) = true
has_single_bit(0b1001) = false
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="popcount"></a>`popcount`

計算設定為不帶正負號整數值之一的位數。
 
```cpp
template<class T>
[[nodiscard]] constexpr int popcount(T value) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要測試的不帶正負號的整數值。

### <a name="return-value"></a>傳回值

數位位設定為其中一個 `value` 。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
   for (unsigned char value = 0; value < 16; value++)
    {
        std::cout << "\npopcount(0b" << std::bitset<4>(value) << ") = "
                  << std::popcount(value);
    }
    return 0;
}
```

```Output
popcount(0b0000) = 0
popcount(0b0001) = 1
popcount(0b0010) = 1
popcount(0b0011) = 2
popcount(0b0100) = 1
popcount(0b0101) = 2
popcount(0b0110) = 2
popcount(0b0111) = 3
popcount(0b1000) = 1
popcount(0b1001) = 2
popcount(0b1010) = 2
popcount(0b1011) = 3
popcount(0b1100) = 2
popcount(0b1101) = 3
popcount(0b1110) = 3
popcount(0b1111) = 4
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="rotl"></a>`rotl`

將不帶正負號整數值的位向左旋轉指定的次數。 「落在」最左邊的位會旋轉到最右邊的位。
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotl(T value, int s) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要旋轉的不帶正負號的整數值。

*！*\
要執行的左方旋轉數目。

### <a name="return-value"></a>傳回值

旋轉左方的結果 `value` `s` 。
如果 `s` 是零，則會傳回 `value` 。
如果 `s` 是負數，則會 `rotr(value, -s)` 。 最右邊位的「落在」位會旋轉到最左邊的位。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 1;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotl(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotl(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotl(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotl(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotl(0b00000001, 1) = 0b00000010
rotl(0b00000010, 1) = 0b00000100
rotl(0b00000100, 1) = 0b00001000
rotl(0b00001000, 1) = 0b00010000
rotl(0b00010000, 1) = 0b00100000
rotl(0b00100000, 1) = 0b01000000
rotl(0b01000000, 1) = 0b10000000
rotl(0b10000000, 1) = 0b00000001
rotl(0b00000001,-1) = 0b10000000
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="rotr"></a>`rotr`

將右邊的位數旋轉 `value` 指定的次數。 最右邊位的「落在」位會旋轉回最左邊的位。
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotr(T value, int s) noexcept;
```

### <a name="parameters"></a>參數

*價值*\
要旋轉的不帶正負號的整數值。

*！*\
要執行的正確旋轉數目。

### <a name="return-value"></a>傳回值

輪替 `value` right、times 的結果 `s` 。
如果 `s` 是零，則會傳回 `value` 。
如果 `s` 是負數，則會 `rotl(value, -s)` 。 最左邊的「落在」位的位會旋轉回最右邊的位。

### <a name="example"></a>範例

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 128;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotr(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotr(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotr(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotr(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotr(0b10000000, 1) = 0b01000000
rotr(0b01000000, 1) = 0b00100000
rotr(0b00100000, 1) = 0b00010000
rotr(0b00010000, 1) = 0b00001000
rotr(0b00001000, 1) = 0b00000100
rotr(0b00000100, 1) = 0b00000010
rotr(0b00000010, 1) = 0b00000001
rotr(0b00000001, 1) = 0b10000000
rotr(0b10000000,-1) = 0b00000001
```

### <a name="remarks"></a>備註

如果 `T` 是不帶正負號的整數類型，則這個範本函式只會參與多載解析。 例如： `unsigned int` 、、 `unsigned long` 、 `unsigned short` 等等 `unsigned char` 。

## <a name="requirements"></a>規格需求

**標頭：**\<bit>

**命名空間：** std

`/std:c++latest` 是必要項

## <a name="see-also"></a>另請參閱

[\<bit>](bit.md)
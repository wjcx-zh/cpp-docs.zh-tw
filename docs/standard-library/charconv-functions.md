---
title: '&lt;charconv &gt; 函式'
description: 描述 <charconv> 將整數或浮點值轉換成字元或從字元轉換的程式庫函數
ms.date: 08/20/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: b8117f2a272f33be2bb5fef6ba8fa53ec794b63b
ms.sourcegitcommit: f1752bf90b4f869633a859ace85439ca19e208b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2020
ms.locfileid: "88722150"
---
# <a name="ltcharconvgt-functions"></a>&lt;charconv &gt; 函式

\<charconv>標頭包含下列非成員函式：

| **非成員函式** | **描述** |
|-|-|
|[to_chars](#to_chars) | 將整數或浮點值轉換為的序列 **`char`** 。 |
|[from_chars](#from_chars) | 將序列轉換 **`char`** 為整數或浮點值。 |

這些轉換函式已針對效能進行調整，也支援最短的往返行為。 最短來回行為表示當數位轉換成字元時，只會寫出足夠的精確度，以在將這些字元轉換回浮點數時復原原始數位。

- 將字元轉換為數字時，數值不需要以 null 終止。 同樣地，將數位轉換成字元時，結果不會以 null 結束。
- 轉換函式不會配置記憶體。 您在所有情況下都擁有緩衝區。
- 轉換函式不會擲回。 系統會傳回結果，您可以從中判斷轉換是否成功。
- 轉換函式不會區分執行時間的舍入模式。
- 轉換函式不會感知地區設定。 它們一律會將小數點列印和剖析為 `'.'` 使用逗號的地區設定，而不是 '，'。

## `to_chars`

將整數或浮點值轉換為的序列 **`char`** 。

藉 `value` 由填滿範圍 \[ `first` `last`) ，其中 \[ `first` `last`) 必須是有效的範圍，以轉換成字元字串。
傳回 [to_chars_result 結構](to-chars-result-structure.md)。 如果轉換成功（如所述）， `to_char_result.ec` 則成員 `ptr` 是所寫入字元的最後一端指標。 否則， `to_char_result.ec` 具有值、 `errc::value_too_large` `to_char_result.ptr` 具有值 `last` ，而且不指定範圍的內容 \[ `first` `last`) 。

`to_chars`如果您提供能力不佳的大型緩衝區來保存結果，則可能會失敗的唯一方法。

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>參數

*第一*\
指向要填滿的緩衝區開頭。

*最後*\
將超過緩衝區結尾的一個字元指向填滿。

*價值*\
要進行轉換的值。 如果 `value` 是負數，表示開頭為 `-` 。

*基地*\
若為整數轉換，則為轉換成字元時要使用的基底 `value` 。 必須介於2到36（含）之間。 不會有前置零。 範圍 10.. 35 (內含) 的數位會以小寫字元 a 表示。Z

*Fmt*\
若為浮點數轉換，則為指定要使用之轉換格式的位元遮罩，例如科學、固定或十六進位。 如需詳細資訊，請參閱 [chars_format](chars-format-class.md) 。

*精度*\
若為浮點數轉換，則為已轉換值的有效位數位數。

### <a name="return-value"></a>傳回值

包含轉換結果的 [to_chars_result](to-chars-result-structure.md) 。

### <a name="remarks"></a>備註

採用 [chars_format](chars-format-class.md) 參數的函式會判斷轉換規範，就像它們使用的方式一樣：如果是，則為，如果為 `printf()` ，則 `'f'` `fmt` `chars_format::fixed` `'e'` `fmt` `chars_format::scientific` `'a'` (不含 `0x` 結果中的前置) 如果 `fmt` 為，則為 `chars_format::hex` ，如果為， `'g'` `fmt` `chars_format::general` 則為。 指定最短的固定標記法可能仍會產生冗長的輸出，因為當值非常大或非常小時可能是最短的標記法。

下表描述不同的和參數組合所提供的轉換行為 `fmt` `precision` 。 「最短來回行為」一詞是指寫入所需的最少數位數目，如此一來，使用對應函式剖析該標記法 `from_chars` 將會完全復原此值。

| `fmt` 和 `precision` 組合 | 輸出 |
|--|--|
|  兩者皆非 | 無論固定或科學記號標記法較短，請以 tiebreaker 的形式進行修正。</br>任何採用參數的多載都無法模擬此行為 `fmt` 。 |
| `fmt` | 指定格式的最短來回行為，例如最短的科學格式。 |
| `fmt` 和 `precision` | 使用指定的有效位數（依照 `printf()` 樣式），不需要最短的往返行為。 |

### <a name="example"></a>範例

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.
    
    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

將序列轉換 **`char`** 為整數或浮點值。

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>參數

*第一*\
指向要轉換之字元緩衝區的開頭。

*最後*\
指向要轉換之字元緩衝區的結尾元素之後的一個。

*價值*\
如果轉換成功，則包含轉換的結果。

*基地*\
若為整數轉換，則為要在轉換期間使用的基底。 必須介於2到36（含）之間。

*Fmt*\
若為浮點數轉換，則為要轉換的字元序列格式。 如需詳細資訊，請參閱 [chars_format](chars-format-class.md) 。

### <a name="remarks"></a>備註

`from_chars()`函數會分析字串 \[ `first` ， `last`) 數位模式，其中) 必須 \[ `first` `last` 是有效的範圍。

剖析字元時，不會忽略空白字元。 `strtod()`例如，緩衝區的開頭必須是有效的數值表示。

傳回 [from_chars_result 結構](from-chars-result-structure.md)。

如果沒有任何字元符合數位模式、 `value` 未修改、 `from_chars_result.ptr` 指向 `first` ，且 `from_chars_result.ec` 為 `errc::invalid_argument` 。

如果只有某些字元符合數位模式， `from_chars_result.ptr` 會指向不符合模式的第一個字元，或 `last` 如果所有字元相符，則會包含參數的值。

如果剖析的值不在類型所表示的範圍中 `value` ， `value` 則不會修改，且 `from_chars_result.ec` 為 `errc::result_out_of_range` 。

否則， `value` 會在四捨五入之後設定為剖析的值，而且 `from_chars_result.ec` 等於 `errc{}` 。

### <a name="example"></a>範例

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="requirements"></a>需求

**標頭：**\<charconv>

**命名空間：** std

/std：需要 c + + 17 或更新版本。

## <a name="see-also"></a>請參閱

[\<charconv>](charconv.md)  
來回往返的[最短十進位字串](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/) 
[printf ( # A1 格式](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)規範
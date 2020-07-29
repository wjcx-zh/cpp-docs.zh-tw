---
title: '&lt;charconv &gt; 函式'
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: 276ac2bce70ce5c4ebf8e22bb1da1ac9914db55e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87246100"
---
# <a name="ltcharconvgt-functions"></a>&lt;charconv &gt; 函式

\<charconv>標頭包含下列非成員函式：

| **非成員函式** | **說明** |
|-|-|
|[to_chars](#to_chars) | 將整數或浮點值轉換為的序列 **`char`** 。 |
|[from_chars](#from_chars) | 將序列轉換成 **`char`** 整數或浮點值。 |

這些轉換函式會針對效能進行微調，同時也支援最短的往返行為。 最短的來回行為表示當數位轉換成字元時，只會寫出足夠的精確度，以在將這些字元轉換回浮點時，能夠復原原始數位。

- 將字元轉換成數位時，數值不需要是以 null 結束。 同樣地，將數位轉換成字元時，結果不會以 null 結束。
- 轉換函式不會配置記憶體。 您在所有情況下都擁有該緩衝區。
- 轉換函式不會擲回。 傳回的結果可供您判斷轉換是否成功。
- 轉換函式不會區分執行時間舍入模式。
- 轉換函式不會感知地區設定。 它們一律 `'.'` 會針對使用逗號的地區設定，將小數點列印和剖析為，而不是 '，'。

## `to_chars`

將整數或浮點值轉換為的序列 **`char`** 。

藉 `value` 由填滿範圍，將轉換成字元字串， \[ `first` `last` 其中 \[ `first` ， `last` ）必須是有效的範圍。
傳回[to_chars_result 結構](to-chars-result-structure.md)。 如果轉換成功（如所示 `to_char_result.ec` ），成員 `ptr` 就是所寫入字元的一個後端指標。 否則， `to_char_result.ec` 具有值， `errc::value_too_large` `to_char_result.ptr` 且值為 `last` ，且範圍的內容未 \[ `first` `last` 指定。

只有 `to_chars` 當您提供能力不佳的大型緩衝區來保存結果時，才會發生失敗的唯一方法。

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

*頭*\
指向要填滿的緩衝區開頭。

*次*\
指向超過緩衝區結尾的一個字元，以填滿。

*value*\
要進行轉換的值。 如果 `value` 是負數，表示的開頭為 `-` 。

*群體*\
針對整數轉換，這是轉換成字元時要使用的基底 `value` 。 必須介於2到36（含）之間。 不會有前置零。 範圍 10.. 35 （含）之間的數位會以小寫字元 a 表示。z

*bcp.fmt*\
對於浮點轉換，這是一個位元遮罩，用來指定要使用的轉換格式，例如科學、固定或十六進位。 如需詳細資訊，請參閱[chars_format](chars-format-class.md) 。

*精密*\
若為浮點轉換，則為已轉換值的精確度位數。

### <a name="return-value"></a>傳回值

包含轉換結果的[to_chars_result](to-chars-result-structure.md) 。

### <a name="remarks"></a>備註

採用[chars_format](chars-format-class.md)參數的函式會決定轉換規範，如同它們使用的方式如下：如果是，則為，如果是，則為，如果是，則為，如果是，則為，如果為，則為 `printf()` `f` `fmt` `chars_format::fixed` `e` `fmt` `chars_format::scientific` `a` `fmt` `chars_format::hex` `g` `fmt` `chars_format::general` 。 指定最短的固定標記法仍然可能導致冗長的輸出，因為此值可能是非常大或非常小的最短可能表示。

下表描述不同的和參數組合所提供的轉換行為 `fmt` `precision` 。 「最短來回行程」一詞指的是寫入所需的最少位數，因此使用對應的函式來剖析該標記法 `from_chars` 將會完全復原此值。

| `fmt`和 `precision` 組合 | 輸出 |
|--|--|
|  兩者皆非 | 不論固定或科學記號標記法是較短的，偏好以 tiebreaker 的形式來修正。</br>任何接受參數的多載都無法模擬此行為 `fmt` 。 |
| `fmt` | 指定格式的最短來回行為，例如最短的科學格式。 |
| `fmt` 和 `precision` | 會使用指定的有效位數（遵循 `printf()` 樣式），而不需要最短的來回行程行為。 |

### <a name="return-value"></a>傳回值

保存轉換結果的[to_chars_result](to-chars-result-structure.md) 。

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

將序列轉換成 **`char`** 整數或浮點值。

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

*頭*\
指向要轉換之字元緩衝區的開頭。

*次*\
指向要轉換之字元緩衝區結尾元素的其中一個。

*value*\
如果轉換成功，則包含轉換的結果。

*群體*\
針對整數轉換，這是轉換期間要使用的基底。 必須介於2到36（含）之間。

*bcp.fmt*\
對於浮點轉換，這是要轉換之字元序列的格式。 如需詳細資訊，請參閱[chars_format](chars-format-class.md) 。

### <a name="remarks"></a>備註

函式會 `from_chars()` 分析字串 \[ `first` ， `last` ）以取得數位模式，其中 \[ `first` ， `last` ）必須是有效的範圍。

剖析字元時，不會忽略空白字元。 與不同的 `strtod()` 是，緩衝區的開頭必須是有效的數值表示。

傳回[from_chars_result 結構](from-chars-result-structure.md)。

如果沒有任何字元符合數位模式， `value` 則會進行未修改、 `from_chars_result.ptr` 指向 `first` ，而 `from_chars_result.ec` 是 `errc::invalid_argument` 。

如果只有部分字元符合數位模式， `from_chars_result.ptr` 會指向不符合模式的第一個字元， `last` 如果所有字元都相符，則會包含參數的值。

如果剖析的值不在類型所表示的範圍內 `value` ， `value` 則不會修改，而且 `from_chars_result.ec` 會是 `errc::result_out_of_range` 。

否則， `value` 會在四捨五入後設定為剖析的值，且 `from_chars_result.ec` 等於 `errc{}` 。

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

## <a name="see-also"></a>另請參閱

[\<charconv>](charconv.md)  
[來回行程的最短十進位字串](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/)
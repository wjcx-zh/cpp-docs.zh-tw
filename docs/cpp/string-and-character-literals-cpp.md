---
title: 字串和字元常值（c + +）
description: 如何在 c + + 中宣告和定義字串和字元常值。
ms.date: 02/18/2020
f1_keywords:
- R
- L
- u
- u8
- LR
- uR
- u8R
helpviewer_keywords:
- literal strings [C++]
- string literals [C++]
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: 60389ecf01cf16b1cf2a86fc68da94bd558b6d83
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231126"
---
# <a name="string-and-character-literals-c"></a>字串和字元常值（c + +）

C++ 支援各種字串和字元類型，並提供方法來表示所有這些類型的常值。 在原始程式碼中，您可以使用字元集表示字元和字串常值的內容。 通用字元名稱和逸出字元允許您只使用基本來源字元集表示任何字串。 原始字串常值可讓您避免使用逸出字元，而且可用來表示所有類型的字串常值。 您也可以建立 `std::string` 常值，而不需要執行額外的結構或轉換步驟。

```cpp
#include <string>
using namespace std::string_literals; // enables s-suffix for std::string literals

int main()
{
    // Character literals
    auto c0 =   'A'; // char
    auto c1 = u8'A'; // char
    auto c2 =  L'A'; // wchar_t
    auto c3 =  u'A'; // char16_t
    auto c4 =  U'A'; // char32_t

    // Multicharacter literals
    auto m0 = 'abcd'; // int, value 0x61626364

    // String literals
    auto s0 =   "hello"; // const char*
    auto s1 = u8"hello"; // const char*, encoded as UTF-8
    auto s2 =  L"hello"; // const wchar_t*
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32

    // Raw string literals containing unescaped \ and "
    auto R0 =   R"("Hello \ world")"; // const char*
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32

    // Combining string literals with standard s-suffix
    auto S0 =   "hello"s; // std::string
    auto S1 = u8"hello"s; // std::string
    auto S2 =  L"hello"s; // std::wstring
    auto S3 =  u"hello"s; // std::u16string
    auto S4 =  U"hello"s; // std::u32string

    // Combining raw string literals with standard s-suffix
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32
}
```

字串常值可以沒有前置詞，或者以 `u8`、 `L`、 `u`和  `U` 前置詞分別表示半形字元 (單一位元組或多位元組)、UTF-8、全形字元 (UCS-2 或 UTF-16)、UTF-16 和 UTF-32 編碼。 原始字串常值可以有 `R` 、 `u8R` 、 `LR` 、和前置詞，適用于 `uR` `UR` 這些編碼的原始版本。  若要建立暫存或靜態 `std::string` 值，您可以使用字串常值或具有尾碼的原始字串常值 `s` 。 如需詳細資訊，請參閱下面的「[字串常](#string-literals)值」一節。 如需基本來源字元集、通用字元名稱，以及使用原始程式碼中的擴充字碼頁字元的詳細資訊，請參閱[character sets](../cpp/character-sets.md)。

## <a name="character-literals"></a>字元常值

*「字元常值」* (character literal) 是由常數字元所組成。 它是以單引號括住的字元來表示。 字元常值有五種類型：

- 類型的一般字元常值 **`char`** ，例如`'a'`

- 類型的 UTF-8 字元常值 **`char`** （ **`char8_t`** c + + 20），例如`u8'a'`

- 類型的寬字元常值 **`wchar_t`** ，例如`L'a'`

- 類型的 UTF-16 字元常值 **`char16_t`** ，例如`u'a'`

- 類型的 UTF-32 字元常值 **`char32_t`** ，例如`U'a'`

用於字元常值的字元可以是任何字元，但保留字元反斜線（ **`\`** ）、單引號（ **`'`** ）或分行符號除外。 使用逸出序列可指定保留字元。 只要類型大到足以容納字元，就可以使用通用字元名稱指定字元。

### <a name="encoding"></a>編碼

字元常值會根據其前置詞以不同的方式進行編碼。

- 不含前置詞的字元常值是一般的字元常值。 包含可以在執行字元集中表示之單一字元、轉義順序或通用字元名稱的一般字元常值，其值會等於其在執行字元集中的編碼數值。 包含一個以上字元、escape 序列或通用字元名稱的一般字元常值是一個*多重字元常*值。 無法在執行字元集中表示的多重字元常值或一般字元常值具有類型 **`int`** ，且其值為執行定義。 如需 MSVC，請參閱下面的**Microsoft 專有**章節。

- 開頭為前置詞的字元常 `L` 值是寬字元常值。 包含單一字元、escape 序列或通用字元名稱的寬字元常值，其值會等於其在執行寬字元集中的編碼數值，除非該字元常值在執行寬字元集中沒有任何標記法，在此情況下，該值為「執行定義」。 包含多個字元、escape 序列或通用字元名稱的寬字元常值，是由實作為定義的。 如需 MSVC，請參閱下面的**Microsoft 專有**章節。

- 開頭為前置詞的字元常 `u8` 值是 utf-8 字元常值。 包含單一字元、escape 序列或通用字元名稱的 UTF-8 字元常值，其值若可由單一 UTF-8 程式碼單位（對應于 C0 控制項和基本拉丁 Unicode 區塊）來表示，則其值會等於其 ISO 10646 碼點值。 如果這個值不能以單一 UTF-8 程式碼單位表示，則程式格式不正確。 包含一個以上字元、escape 序列或通用字元名稱的 UTF-8 字元常值格式不正確。

- 開頭為前置詞的字元常 `u` 值是 utf-16 字元常值。 包含單一字元、escape 序列或通用字元名稱的 UTF-16 字元常值，如果可以由單一 UTF-16 程式碼單位（對應至基本多語言平面）表示，則其值會等於其 ISO 10646 代碼點值。 如果這個值不能以單一 UTF-16 程式碼單位表示，則程式格式不正確。 包含一個以上字元、escape 序列或通用字元名稱的 UTF-16 字元常值格式不正確。

- 開頭為前置詞的字元常 `U` 值是 UTF-32 字元常值。 包含單一字元、escape 序列或通用字元名稱的 UTF-32 字元常值，其值會等於其 ISO 10646 程式碼點值。 包含一個以上字元、escape 序列或通用字元名稱的 UTF-32 字元常值格式不正確。

### <a name="escape-sequences"></a><a name="bkmk_Escape"></a>Escape 序列

逸出序列有三種：簡單的、八進位和十六進位。 Escape 序列可以是下列其中一個值：

|值|逸出序列|
|-----------|---------------------|
| 新行字元 | \\n |
| 反斜線 | \\\\ |
| 水平定位字元 | \\t |
| 問號 | ? 或 \\? |
| 垂直定位字元 | \\& |
| 單引號 | \\' |
| 退格鍵 | \\位元組 |
| 雙引號 | \\" |
| 歸位字元 | \\r |
| null 字元 | \\0 |
| 換頁字元 | \\f |
| 八進位 | \\ooo |
| 警示 (鈴聲) | \\a |
| 十六進位 | \\xhhh |

八進位的逸出序列是反斜線，後面接著一連串的一到三個八進位數位。 如果比第三個數字更早發生，八進位逸出序列會在不是八進位數位的第一個字元終止。 可能的最大八進位值為 `\377` 。

十六進位的逸出序列是反斜線，後面接著字元 `x` ，後面接著一或多個十六進位數位的序列。 系統會忽略前置零。 在一般或 u8 首碼的字元常值中，最高的十六進位值是0xFF。 在 L 前置詞或 u 前置詞的全形字元常值中，最高的十六進位值是 0xFFFF。 在 U 前置詞的全形字元常值中，最高的十六進位值是 0xFFFFFFFF。

這個範例程式碼會顯示一些使用一般字元常值的逸出字元範例。 相同的轉義順序語法對其他字元常數值型別而言是有效的。

```cpp
#include <iostream>
using namespace std;

int main() {
    char newline = '\n';
    char tab = '\t';
    char backspace = '\b';
    char backslash = '\\';
    char nullChar = '\0';

    cout << "Newline character: " << newline << "ending" << endl;
    cout << "Tab character: " << tab << "ending" << endl;
    cout << "Backspace character: " << backspace << "ending" << endl;
    cout << "Backslash character: " << backslash << "ending" << endl;
    cout << "Null character: " << nullChar << "ending" << endl;
}
/* Output:
Newline character:
ending
Tab character:  ending
Backspace character:ending
Backslash character: \ending
Null character:  ending
*/
```

反斜線字元（ **`\`** ）是放在行尾時的行接續字元。 如果您想要讓反斜線字元顯示為字元常值，您必須在資料列中輸入兩個反斜線（ **`\\`** ）。 如需行接續字元的詳細資訊，請參閱 [Phases of Translation](../preprocessor/phases-of-translation.md)。

#### <a name="microsoft-specific"></a>Microsoft 專有

若要從窄多重字元常值建立值，編譯器會將單引號之間的字元或字元序列轉換成32位整數內的8位值。 常值中的多個字元，會視需要從高序位到低序位填入對應的位元組。 然後編譯器會依照一般規則，將整數轉換成目的地類型。 例如，若要建立 **`char`** 值，編譯器會採用低序位位元組。 若要建立 **`wchar_t`** 或 **`char16_t`** 值，編譯器會採用低序位字組。 如果任何位元設定高出指定的位元組或字組，編譯器會警告結果遭截斷。

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
int i0     = 'abcd';    // 0x61626364
```

會將超過三位數的八進位 escape 序列視為3位數的八進位序列，後面接著後續的數位做為多重字元常值中的字元，這可能會產生令人驚訝的結果。 例如：

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

似乎包含非八進位字元的 Escape 序列會評估為最後一個八進位字元的八進位序列，後面接著其餘字元做為多重字元常值中的後續字元。 如果第一個非八進位字元是十進位數，則會產生警告 C4125。 例如：

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

值大於的八進位逸出序列 `\377` 會導致錯誤 C2022： '*值-十進位*'：字元太大。

具有十六進位和非十六進位字元的 escape 序列會評估為多重字元常值，其中包含最多到最後一個十六進位字元的十六進位逸出序列，後面接著非十六進位字元。 不包含十六進位數位的十六進位逸出序列會導致編譯器錯誤 C2153：「十六進位常值至少必須有一個十六進位數位」。

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

如果在前面加上的寬字元常 `L` 值包含多重字元序列，則會從第一個字元取得該值，而編譯器會引發警告 C4066。 系統會忽略後續的字元，不同于對等的一般多重字元常值的行為。

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

Microsoft 專屬章節將**于**此結束。

### <a name="universal-character-names"></a><a name="bkmk_UCN"></a> 通用字元名稱

在字元常值和原生 (非原始) 的字串常值中，任何字元都可能使用通用字元名稱表示。  通用字元名稱是由前置片語成 `\U` ，後面接著八位數的 unicode 程式碼片段，或前置詞 `\u` 後面接著四位數的 unicode 程式碼點。 所有的八位數或四位數，都一定要出現才是格式正確的通用字元名稱。

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Surrogate 字組

通用字元名稱無法編碼代理程式碼點範圍 D800-DFFF 中的值。 至於 Unicode surrogate 字組，請使用 `\UNNNNNNNN`指定通用字元名稱，這裡的 NNNNNNNN 為字元的八位數字碼指標。 必要時，編譯器會產生代理配對。

過去在 C++03 中，語言只允許由其通用字元名稱所代表的字元子集，以及未實際代表任何有效 Unicode 字元的一些通用字元名稱。 此錯誤已在 c + + 11 標準中修正。 在 C++11 中，字元和字串常值及識別項可以使用通用字元名稱。  如需通用字元名稱的詳細資訊，請參閱 [Character Sets](../cpp/character-sets.md)。 如需 Unicode 的詳細資訊，請參閱 [Unicode](/windows/win32/intl/unicode)。 如需 Surrogate 字組的詳細資訊，請參閱 [Surrogate 字組和補充字元](/windows/win32/Intl/surrogates-and-supplementary-characters)。

## <a name="string-literals"></a><a name="string-literals"></a>字串常值

字串常值代表構成 null 結束字串的一連串字元。 這些字元必須使用雙引號括起來。 有下列字串常值類型：

### <a name="narrow-string-literals"></a>窄字串常值

窄字串常值是類型的非前置詞、雙引號分隔、null 結束陣列 `const char[n]` ，其中 n 是陣列的長度（以位元組為單位）。 半形字串常值可能包含任何圖形字元，但雙引號 (`"`)、反斜線 (`\`) 或新行字元除外。 半形字串常值也可能包含上文列出的逸出序列，以及符合一個位元組大小的通用字元名稱。

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>UTF-8 編碼的字串

UTF-8 編碼的字串是 u8 前置詞、以雙引號分隔、以 null 結束的類型陣列 `const char[n]` ，其中*n*是已編碼陣列的長度（以位元組為單位）。 u8 前置字串常值可以包含任何圖形字元，但雙引號 (`"`)、反斜線 (`\`) 或新行字元除外。 u8 前置字串常值也可以包含上列逸出序列，以及任何通用字元名稱。

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>寬字元串常值

寬字元串常值是以 null 結束的常數陣列， **`wchar_t`** 前面會加上 ' `L` '，並包含雙引號（ **`"`** ）、反斜線（ **`\`** ）或分行符號以外的任何圖形字元。 全形字串常值可以包含上列逸出序列，以及任何通用字元名稱。

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16_t-and-char32_t-c11"></a>char16_t 和 char32_t (C++11)

C + + 11 引進可攜 **`char16_t`** （16位 unicode）和 **`char32_t`** （32位 unicode）字元類型：

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>原始字串常值（c + + 11）

原始字串常值是以 null 結束的陣列（任何字元類型），其中包含任何圖形字元，包括雙引號（ **`"`** ）、反斜線（ **`\`** ）或換行字元。 原始字串常值通常用於使用字元類別的規則運算式，以及 HTML 字串和 XML 字串。 如需範例，請參閱下列文章： [Bjarne Stroustrup 的 C++11 常見問題集](http://www.stroustrup.com/C++11FAQ.html)。

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

「分隔符號」是一種使用者定義的序列，最多16個字元，緊接在原始字串常值的左括弧前面，然後緊接在其右括弧後面。  例如， `R"abc(Hello"\()abc"` 中的分隔符號順序是 `abc` ，字串內容是 `Hello"\(`。 您可以使用分隔符號，釐清包含雙引號和括號的原始字串。 這個字串常值會造成編譯器錯誤：

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

但是分隔符號解決這個錯誤：

```cpp
const char* good_parens = R"xyz()")xyz";
```

您可以在來源中，建立包含分行符號（而不是逸出字元）的原始字串常值：

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>std：： string 常值（c + + 14）

`std::string`常值是使用者定義常值的標準程式庫執行（如下所示），以表示為 `"xyz"s` （ `s` 尾碼）。 這種字串常值 `std::string` `std::wstring` `std::u32string` `std::u16string` 會根據指定的前置詞，產生類型為、、或的暫存物件。 如果未使用前置詞， `std::string` 則會產生。 `L"xyz"s`產生 `std::wstring` 。 `u"xyz"s`會產生[std：： u16string](../standard-library/string-typedefs.md#u16string)，並 `U"xyz"s` 產生[std：： u32string](../standard-library/string-typedefs.md#u32string)。

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

`s`尾碼也可以用於原始字串常值：

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

`std::string`常值是在標頭檔的命名空間中定義 `std::literals::string_literals` \<string> 。 因為 `std::literals::string_literals` 、和 `std::literals` 都宣告為[內嵌命名空間](../cpp/namespaces-cpp.md)，所以會 `std::literals::string_literals` 自動將視為直接屬於命名空間 `std` 。

### <a name="size-of-string-literals"></a>字串常值的大小

針對 ANSI `char*` 字串和其他單一位元組編碼（但不是 utf-8），字串常值的大小（以位元組為單位）是結束的 null 字元的字元數加1。 對於所有其他字串類型，大小不會與字元數完全相關。 UTF-8 使用最多四個 **`char`** 元素來編碼某些程式*代碼單位*， **`char16_t`** 或 **`wchar_t`** 編碼為 utf-16 可能會使用兩個元素（總共四個位元組）來編碼單一程式*代碼單位*。 本例顯示全形字串常值以位元組為單位的大小：

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

請注意， `strlen()` 和 `wcslen()` 不包括結束 null 字元的大小，其大小等於字串類型的專案大小：或字串上的一個位元組 `char*` `char8_t*` 、兩個位元組的 `wchar_t*` 或 `char16_t*` 字串，以及字串的四個位元組 `char32_t*` 。

字串常值的最大長度是65535個位元組。 這個限制適用於半形字串常值和全形字串常值。

### <a name="modifying-string-literals"></a>修改字串常值

因為字串常值（不包括 `std::string` 常值）是常數，所以嘗試修改它們（例如） `str[2] = 'A'` 會造成編譯器錯誤。

#### <a name="microsoft-specific"></a>Microsoft 專有

在 Microsoft c + + 中，您可以使用字串常值來初始化非 const 或的指標 **`char`** **`wchar_t`** 。 C99 程式碼允許此非 const 初始化，但在 c + + 98 中已被取代，並已在 c + + 11 中移除。 嘗試修改字串造成存取違規，如此範例所示：

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

當您設定[ `/Zc:strictStrings` （停用字串常數值型別轉換）](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)編譯器選項時，如果字串常值轉換為非 const 字元指標，您可以讓編譯器發出錯誤。 我們建議使用標準相容的可攜式程式碼。 使用關鍵字來宣告字串常值初始化的指標也是很好的作法 **`auto`** ，因為它會解析為正確的（const）型別。 例如，這個程式碼範例會攔截在編譯時期嘗試寫入字串常值的動作：

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

在某些情況下，可以結合相同字串常值來節省可執行檔中的空間。 在字串常值共用中，編譯器會讓特定字串常值的所有參考指向記憶體內部相同位置，而不是讓每個參考都指向字串常值的個別執行個體。 若要啟用字串共用，請使用 [`/GF`](../build/reference/gf-eliminate-duplicate-strings.md) 編譯器選項。

Microsoft 專屬章節將**于**此結束。

### <a name="concatenating-adjacent-string-literals"></a>串連相鄰的字串常值

會串連相鄰的全形或半形字串常值。 這個宣告：

```cpp
char str[] = "12" "34";
```

等同於此宣告：

```cpp
char atr[] = "1234";
```

以及這個宣告：

```cpp
char atr[] =  "12\
34";
```

使用內嵌十六進位逸出程式碼指定字串常值可能造成未預期的結果。 下列範例是要建立包含 ASCII 5 字元的字串常值，後面接著字元 f、i、v 和 e：

```cpp
"\x05five"
```

實際結果是十六進位 5F (即底線字元的 ASCII 碼)，後面接 i、v、e 字元。 若要取得正確的結果，您可以使用下列其中一個 escape 序列：

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

`std::string`常值（因為它們是 `std::string` 類型）可以與 **`+`** 為類型定義的運算子串連 [`basic_string`](../standard-library/basic-string-class.md) 。 它們的串連方式也與相鄰字串常值相同。 在這兩種情況下，字串編碼和後置詞必須相符：

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>含通用字元名稱的字串常值

原生 (非原始) 的字串常值可以使用通用字元名稱來代表任何字元，只要通用字元名稱可以編碼為字串類型中的一或多個字元。  例如，代表擴充字元的通用字元名稱無法使用 ANSI 字碼頁以窄字串編碼，但是可以在某些多位元組字碼頁或 UTF-8 字串或寬字元串中，以窄字串編碼。 在 c + + 11 中，Unicode 支援是由 `char16_t*` 和 `char32_t*` 字串類型擴充：

```cpp
// ASCII smiling face
const char*     s1 = ":-)";

// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";

// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)
const char*     s3 = u8"😇 = \U0001F607 is O:-)";

// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)
const char16_t* s4 = u"😃 = \U0001F603 is :-D";

// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)
const char32_t* s5 = U"😎 = \U0001F60E is B-)";
```

## <a name="see-also"></a>另請參閱

[字元集](../cpp/character-sets.md)\
[數值、布林值和指標常值](../cpp/numeric-boolean-and-pointer-literals-cpp.md)\
[使用者定義常值](../cpp/user-defined-literals-cpp.md)

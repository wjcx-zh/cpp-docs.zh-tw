---
title: 使用者定義常值（C++）
description: 說明標準C++中使用者定義常值的用途和使用方式。
ms.date: 02/10/2020
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: a6636be414fa4dc199ce10fca1b33f092492575f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2020
ms.locfileid: "79090558"
---
# <a name="user-defined-literals"></a>使用者定義常值

中C++有六個主要的常值類別：整數、字元、浮點、字串、布林值和指標。 從C++ 11 開始，您可以根據這些類別定義您自己的常值，以提供一般慣用語的語法快捷方式並增加型別安全。 例如，假設您有一個 `Distance` 類別。 您可以定義公里的常值和另一個代表英里的文字，並藉由撰寫下列內容來鼓勵使用者明確瞭解測量單位： `auto d = 42.0_km` 或 `auto d = 42.0_mi`。 使用者定義的常值沒有任何效能優勢或缺點;它們主要是為了方便或編譯時間類型推斷。 標準程式庫具有 `std::string`、`std::complex`的使用者定義常值，以及 \<chrono > 標頭中時間和持續時間作業的單位：

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>使用者定義常值運算子簽章

您可以使用下列其中一種形式，在命名空間範圍定義**運算子 ""** ，以執行使用者定義的常值：

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

先前範例中的運算子名稱都是您所提供名稱的預留位置；不過，需要前置底線。 （只允許標準程式庫定義不含底線的常值）。傳回類型是您自訂轉換或常值所執行之其他作業的位置。 而且，所有這些運算子都可以定義為 `constexpr`。

## <a name="cooked-literals"></a>處理後的常值

在原始程式碼中，不論使用者定義的任何常值，基本上都是一連串的英數位元，例如 `101`或 `54.7`，或是 `"hello"` 或 `true`。 編譯器會將序列解讀為整數、浮點數、const char\* 字串等等。 使用者定義的常值，它會接受指派給常值的任何型別做為輸入，非正式稱為*處理後常*值。 所有上面的運算子 (`_r` 和 `_t` 除外) 都是處理後的常值。 例如，常值 `42.0_km` 會繫結至簽章與 _b 類似的 _km 運算子，常值 `42_km` 則繫結至簽章與 _a 類似的運算子。

下列範例示範使用者定義常值如何鼓勵呼叫端明確指定其輸入。 若要建構 `Distance`，使用者必須使用適當的使用者定義常值來明確指定公里或英哩。 您可以用其他方式達到相同的結果，但使用者定義的常值比替代方案的詳細資訊還少。

```cpp
// UDL_Distance.cpp

#include <iostream>
#include <string>

struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double val);
    friend Distance operator"" _mi(long double val);

    long double kilometers{ 0 };
public:
    const static long double km_per_mile;
    long double get_kilometers() { return kilometers; }

    Distance operator+(Distance other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

const long double Distance::km_per_mile = 1.609344L;

Distance operator"" _km(long double val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * Distance::km_per_mile);
}

int main()
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    std::cout << "Kilometers in d: " << d.get_kilometers() << std::endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    std::cout << "Kilometers in d2: " << d2.get_kilometers() << std::endl;  //646.956

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    std::cout << "d3 value = " << d3.get_kilometers() << std::endl; // 99.9364

    // Distance d4(90.0); // error constructor not accessible

    std::string s;
    std::getline(std::cin, s);
    return 0;
}
```

常值數位必須使用十進位。 否則，此數位會被視為整數，而類型也不會與運算子相容。 對於浮點輸入，類型必須是**long double**，而對於整數類型，其**長度**必須很長。

## <a name="raw-literals"></a>原始常值

在未經處理的使用者定義常值中，您定義的運算子會接受常值做為 char 值的序列。 您必須以數位或字串或其他類型來解讀該序列。 在此頁面上先前顯示的運算子清單中，`_r` 和 `_t` 可以用來定義原始常值：

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

您可以使用原始常值來提供輸入序列的自訂轉譯，這與編譯器的一般行為不同。 例如，您可以定義將序列 `4.75987` 轉換為自訂 Decimal 類型的常值，而不是 IEEE 754 浮點類型。 原始常值（例如處理後常值）也可以用於輸入序列的編譯階段驗證。

### <a name="example-limitations-of-raw-literals"></a>範例：原始常值的限制

原始常值運算子和常值運算子樣板只適用於整數和浮點使用者定義常值 (如下列範例所示)：

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```

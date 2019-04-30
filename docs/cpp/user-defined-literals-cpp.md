---
title: 使用者定義常值 (C++)
ms.date: 11/04/2016
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: 1de94b43423bb5b420be29d3cace146e265a1459
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392111"
---
# <a name="user-defined-literals--c"></a>使用者定義常值 (C++)

常值有六種主要分類：整數、字元、浮點、字串、布林值和指標。  從 C++ 11 開始，您可以根據這些分類來定義專屬常值，以提供常見慣用語的語法捷徑，並提升類型安全。 例如，假設您有一個 Distance 類別。 您可以針對公里定義一個常值，以及針對英哩定義另一個常值，並鼓勵使用者只要撰寫下列項目來明確指定度量單位：auto d = 42.0_km 或 auto d = 42.0_mi。 使用者定義常值沒有任何效能優勢或缺點；它們主要是為了方便起見，或針對編譯時間類型推斷。 標準程式庫中的時間和持續時間作業中有使用者定義常值的 std: string、 std:: string，和單位\<chrono > 標頭：

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
    complex<double> num =
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>使用者定義常值運算子簽章

定義實作使用者定義常值**運算子""** 在命名空間範圍，以下列格式之一：

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const     char*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const  wchar_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

先前範例中的運算子名稱都是您所提供名稱的預留位置；不過，需要前置底線。 (只允許「標準程式庫」定義沒有底線的常值。)傳回類別可讓您自訂轉換或常值所執行的其他作業。 而且，所有這些運算子都可以定義為 `constexpr`。

## <a name="cooked-literals"></a>處理後的常值

在原始程式碼中，任何常值 (不論是否由使用者定義) 基本上是一連串的英數字元 (例如 `101` 或 `54.7`，或者 `"hello"` 或 `true`)。 編譯器會解譯為整數、 float、 const char 序列\*字串，並依此類推。 使用者定義的常值類型指派給常值，編譯器接受做為輸入，非正式地稱為*處理後的常值*。 所有上面的運算子 (`_r` 和 `_t` 除外) 都是處理後的常值。 例如，常值 `42.0_km` 會繫結至簽章與 _b 類似的 _km 運算子，常值 `42_km` 則繫結至簽章與 _a 類似的運算子。

下列範例示範使用者定義常值如何鼓勵呼叫端明確指定其輸入。 若要建構 `Distance`，使用者必須使用適當的使用者定義常值來明確指定公里或英哩。 當然，使用其他方式也可以達到相同的結果，但使用者定義常值與替代方式相較之下較為簡單。

```cpp
struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double  val);
    friend Distance operator"" _mi(long double val);
    long double kilometers{ 0 };
public:
    long double get_kilometers() { return kilometers; }
    Distance operator+(Distance& other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

Distance operator"" _km(long double  val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * 1.6);
}
int main(int argc, char* argv[])
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6

    // Distance d4(90.0); // error constructor not accessible

    string s;
    getline(cin, s);
    return 0;
}
```

請注意，常值數字必須使用小數點，否則數字會解譯為整數，而類型會與運算子不相容。 也請注意，浮點輸入類型必須是**長雙精度**，以及它必須是整數類資料類型**long long**。

## <a name="raw-literals"></a>原始常值

在原始使用者定義常值中，您定義的運算子會接受一連串 char 值的常值，而且由您決定是否將該序列解譯為數字或字串或是其他類型。 在此頁面上先前顯示的運算子清單中，`_r` 和 `_t` 可以用來定義原始常值：

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

您可以使用原始常值，來提供與編譯器所執行輸入序列不同之輸入序列的自訂解譯。 例如，您可以定義將序列 `4.75987` 轉換為自訂 Decimal 類型的常值，而不是 IEEE 754 浮點類型。 原始常值 (例如處理後的常值) 也可以用來執行輸入序列的編譯時期驗證。

### <a name="example-limitations-of-raw-literals"></a>範例：原始常值限制

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
---
title: decltype （C++）
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 1ed07b8987df7b621ea2809409069cc1121fa24f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180208"
---
# <a name="decltype--c"></a>decltype （C++）

**Decltype**類型規範會產生指定之運算式的類型。 **Decltype**類型規範與[auto 關鍵字](../cpp/auto-cpp.md)，主要適用于撰寫範本庫的開發人員。 使用**auto**和**decltype**宣告樣板函式，其傳回類型取決於其樣板引數的類型。 或者，您可以使用**auto**和**decltype**來宣告包裝呼叫另一個函式的樣板函式，然後傳回已包裝函式的傳回型別。

## <a name="syntax"></a>語法

```
decltype( expression )
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*expression*|運算式。 如需詳細資訊，請參閱[運算式](../cpp/expressions-cpp.md)。|

## <a name="return-value"></a>傳回值

*運算式*參數的類型。

## <a name="remarks"></a>備註

**Decltype**類型規範在 Visual Studio 2010 或更新版本中受到支援，而且可以搭配機器碼或 managed 程式碼使用。 Visual Studio 2015 和更新版本支援 `decltype(auto)` (C++14)。

編譯器會使用下列規則來決定*運算式*參數的型別。

- 如果*expression*參數是識別碼或[類別成員存取](../cpp/member-access-operators-dot-and.md)，`decltype(expression)` 是依*expression*命名之實體的類型。 如果沒有這類實體，或*運算式*參數命名為一組多載函式，則編譯器會產生錯誤訊息。

- 如果*expression*參數是對函式或多載運算子函數的呼叫，`decltype(expression)` 就是函式的傳回型別。 在多載運算子周圍的括號會被忽略。

- 如果*expression*參數是[右](../cpp/lvalues-and-rvalues-visual-cpp.md)值，`decltype(expression)` 是*運算式*的類型。 如果*expression*參數是[左](../cpp/lvalues-and-rvalues-visual-cpp.md)值，`decltype(expression)` 是*運算式*類型的[左值參考](../cpp/lvalue-reference-declarator-amp.md)。

下列程式碼範例示範**decltype**類型規範的一些用法。 首先，假設您撰寫了下列陳述式。

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

接下來，檢查下表中四個**decltype**語句所傳回的類型。

|引數|類型|注意|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|**Const int**的[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md)。|
|`decltype(var);`|**int**|變數 `var` 的類型。|
|`decltype(a->x);`|**double**|成員存取的類型。|
|`decltype((a->x));`|`const double&`|括號內的陳述式會評估為運算式而不是成員存取。 而且因為 `a` 宣告為 `const` 指標，所以該類型是**const double**的參考。|

## <a name="decltype-and-auto"></a>Decltype 和 Auto

在 c + + 14 中，您可以使用沒有尾端傳回類型的 `decltype(auto)` 來宣告其傳回類型取決於其樣板引數類型的範本函式。

在 c + + 11 中，您可以在尾端傳回類型上使用**decltype**類型規範，並搭配**auto**關鍵字來宣告其傳回類型取決於其樣板引數類型的樣板函式。 例如，請考慮下列程式碼範例，其中樣板函式的傳回型別取決於樣板引數的類型。 在程式碼範例中，*未知*的預留位置表示不能指定傳回類型。

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

引進**decltype**類型規範可讓開發人員取得範本函式所傳回之運算式的類型。 使用稍後顯示的*替代函式宣告語法*、 **auto**關鍵字和**decltype**類型規範，以宣告*晚期指定的*傳回類型。 晚期指定的傳回類型是在編譯宣告時決定，而不是在撰寫程式時決定。

下列原型說明替代函式宣告的語法。 請注意， **const**和**volatile**限定詞和擲回**throw** [例外狀況規格](../cpp/exception-specifications-throw-cpp.md)是選擇性的。 *Function_body*預留位置代表指定函式功能的複合陳述式。 在*function_body*中， **decltype**語句中的*運算式*預留位置應符合傳回語句（如果有的話 **）所指定**的運算式，這是最佳的編碼做法。

**auto** *function_name* **（** *parameters*<sub>opt</sub> **）** **const**<sub>opt</sub> **volatile**<sub>opt</sub> **->** **decltype （** *expression* **）** **throw**<sub>opt</sub> **{** *function_body* **};**

下列程式碼範例中，`myFunc` 樣板函式的晚期指定傳回類型由 `t` 和 `u` 樣板引數的類型決定。 程式碼範例是最佳的編碼做法，也會使用右值參考和支援*完美轉送*的 `forward` 函式範本。 如需詳細資訊，請參閱[右值參考宣告子：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>decltype 和轉送函式 (C++11)

轉送函式會包裝對其他函式的呼叫。 試想一個轉送其引數，或者包含這些引數的運算式結果到其他函式的函式樣板。 此外，轉送函式會傳回呼叫其他函式的結果。 在這個案例中，轉送函式的傳回類型應該會與包裝函式的傳回類型相同。

在此案例中，您無法撰寫不含**decltype**類型規範的適當類型運算式。 **Decltype**類型規範會啟用泛型轉送函式，因為它不會遺失有關函數是否傳回參考型別的必要資訊。 如需轉送函式的程式碼範例，請參閱先前的 `myFunc` 樣板函式範例。

## <a name="example"></a>範例

下列程式碼範例會宣告樣板函式 `Plus()` 的晚期指定傳回型別。 `Plus` 函式會使用**運算子 + 多**載來處理它的兩個運算元。 因此，加號運算子 (+) 的解譯和 `Plus` 函式的傳回類型取決於函式引數的類型。

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>範例

**Visual Studio 2017 和更新版本：** 編譯器會在宣告範本而不是具現化時剖析 decltype 引數。 因此，如果在 decltype 引數中找到非相依特製化，則不會延遲到具現化期間，並且會立即處理，而且會在當下診斷出任何產生的錯誤。

下列範例顯示在宣告時引發的這類編譯器錯誤︰

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>需求

Visual Studio 2010 或更新版本。

`decltype(auto)` 需要 Visual Studio 2015 或更新版本。

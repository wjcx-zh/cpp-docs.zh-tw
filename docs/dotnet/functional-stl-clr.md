---
title: 功能 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 996e0f4bcf515d7bc38f89c291927a5444f5654b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423532"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

包含 STL/CLR 標頭`<cliext/functional>`來定義範本類別和相關的範本委派和函式的數目。

## <a name="syntax"></a>語法

```
#include <functional>
```

## <a name="requirements"></a>需求

**標頭：** \<cliext/功能 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|Delegate - 委派|描述|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|兩個引數的委派。|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|兩個引數傳回的委派**void**。|
|[unary_delegate (STL/CLR)](#unary_delegate)|其中一個引數的委派。|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|傳回的單一引數委派**void**。|

|類別|描述|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|要變換正負號的雙引數的仿函式的函式。|
|[binder1st (STL/CLR)](#binder1st)|若要繫結至兩個引數的仿函式的第一個引數的函式。|
|[binder2nd (STL/CLR)](#binder2nd)|第二個引數繫結至兩個引數的仿函式的函式。|
|[divides (STL/CLR)](#divides)|將分割仿函式。|
|[equal_to (STL/CLR)](#equal_to)|相等比較函式。|
|[greater (STL/CLR)](#greater)|更高的比較函式。|
|[greater_equal (STL/CLR)](#greater_equal)|大於或等於比較仿函式。|
|[less (STL/CLR)](#less)|較少的比較函式。|
|[less_equal (STL/CLR)](#less_equal)|小於或等於的比較函式。|
|[logical_and (STL/CLR)](#logical_and)|邏輯 AND 仿函式。|
|[logical_not (STL/CLR)](#logical_not)|邏輯不仿函式。|
|[logical_or (STL/CLR)](#logical_or)|邏輯 OR 仿函式。|
|[minus (STL/CLR)](#minus)|減去仿函式。|
|[modulus (STL/CLR)](#modulus)|模數仿函式。|
|[multiplies (STL/CLR)](#multiplies)|Multiply 仿函式。|
|[negate (STL/CLR)](#negate)|傳回否定其引數的函式。|
|[not_equal_to (STL/CLR)](#not_equal_to)|不等於的比較函式。|
|[plus (STL/CLR)](#plus)|新增仿函式。|
|[unary_negate (STL/CLR)](#unary_negate)|要變換正負號的單一引數的仿函式的函式。|

|功能|描述|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|會產生 binder1st 引數和仿函式。|
|[bind2nd (STL/CLR)](#bind2nd)|會產生 binder2nd 引數和仿函式。|
|[not1 (STL/CLR)](#not1)|會產生 unary_negate 的仿函式。|
|[not2 (STL/CLR)](#not2)|會產生 binary_negate 的仿函式。|

## <a name="members"></a>成員

## <a name="binary_delegate"></a> binary_delegate (STL/CLR)

Genereic 類別會描述兩個引數的委派。 您在使用指定的委派，根據其引數和傳回類型。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>參數

*arg1*<br/>
第一個引數型別。

*Arg2*<br/>
第二個引數的類型。

*結果*<br/>
傳回型別。

### <a name="remarks"></a>備註

Genereic 委派描述兩個引數的函式。

請注意，針對：

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

型別`Fun1`和`Fun2`是同義字，而為：

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

它們不是相同的型別。

### <a name="example"></a>範例

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn (STL/CLR)

Genereic 類別描述兩個引數的委派，會傳回**void**。 您在使用指定的委派，根據其引數。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>參數

*arg1*<br/>
第一個引數型別。

*Arg2*<br/>
第二個引數的類型。

### <a name="remarks"></a>備註

Genereic 委派描述兩個引數函式會傳回**void**。

請注意，針對：

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

型別`Fun1`和`Fun2`是同義字，而為：

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

它們不是相同的型別。

### <a name="example"></a>範例

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate"></a> binary_negate (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回邏輯不是其預存的兩個引數函式。 您在使用指定的函式物件，根據其預存的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*樂趣*<br/>
預存的仿函式的型別。

## <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|
|stored_function_type|仿函式的型別。|

|成員|描述|
|------------|-----------------|
|binary_negate|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type^()|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數仿函數時，會儲存其他兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回邏輯不是預存的仿函式呼叫使用兩個引數。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st"></a> bind1st (STL/CLR)

會產生`binder1st`引數和仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>範本參數

*引數*<br/>
引數型別。

*樂趣*<br/>
仿函式的型別。

#### <a name="function-parameters"></a>函式參數

*仿函式*<br/>
包裝函式。

*left*<br/>
第一個引數，用來包裝。

### <a name="remarks"></a>備註

範本函式會傳回[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`。 您可以使用它作為便利的方式來將兩個引數的仿函式和其第一個引數包裝在單一引數仿函數時，呼叫以第二個引數。

### <a name="example"></a>範例

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd"></a> bind2nd (STL/CLR)

會產生`binder2nd`引數和仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>範本參數

*引數*<br/>
引數型別。

*樂趣*<br/>
仿函式的型別。

#### <a name="function-parameters"></a>函式參數

*仿函式*<br/>
包裝函式。

*right*<br/>
第二個引數，用來包裝。

### <a name="remarks"></a>備註

範本函式會傳回[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`。 您可以使用它作為便利的方式來將兩個引數的仿函式和其第二個引數包裝在單一引數函式呼叫與第一個引數。

### <a name="example"></a>範例

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st"></a> binder1st (STL/CLR)

此範本類別描述單一引數的仿函式，呼叫時，會傳回其預存的雙引數函式呼叫其預存的第一個引數與所提供的第二個引數。 您在使用指定的函式物件，根據其預存的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*樂趣*<br/>
預存的仿函式的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|
|stored_function_type|仿函式的型別。|

|成員|描述|
|------------|-----------------|
|binder1st|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type^()|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述單一引數仿函數時，會儲存兩個引數的仿函式和第一個引數。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回呼叫預存的仿函數與預存的第一個引數和所提供的第二個引數的結果。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd"></a> binder2nd (STL/CLR)

此範本類別描述單一引數的仿函式，呼叫時，會傳回其預存的兩個引數仿函數呼叫所提供的第一個引數和其預存的第二個引數。 您在使用指定的函式物件，根據其預存的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*樂趣*<br/>
預存的仿函式的型別。

## <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|
|stored_function_type|仿函式的型別。|

|成員|描述|
|------------|-----------------|
|binder2nd|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type^()|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述單一引數仿函數時，會儲存兩個引數的仿函式和第二個引數。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回呼叫的預存的第二個引數所提供的第一個引數與預存的仿函式的結果。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides"></a> 除以 (STL/CLR)

此範本類別描述仿函式，呼叫時，傳回第一個引數除以第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數和傳回值類型。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|divides|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type^()|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回第一個引數除以第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to"></a> equal_to (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 只有第一個引數是等於第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|equal_to|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type^()|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否等於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater"></a> 大於 (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 的第一個引數大於第二個時，才。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|greater|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否大於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal"></a> greater_equal (STL/CLR)

此範本類別描述仿函式，呼叫時，只會傳回 true 的第一個引數是否大於或等於第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|greater_equal|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否大於或等於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less"></a> 較少 (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 只有當第一個引數小於第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|less|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否小於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal"></a> less_equal (STL/CLR)

此範本類別描述仿函式，呼叫時，只會傳回 true 的第一個引數是否小於或等於第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|less_equal|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否小於或等於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and"></a> logical_and (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 的第一個引數和第二項測試為 true 時，才。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|logical_and|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數和做為第二項測試為 true。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not"></a> logical_not (STL/CLR)

此範本類別描述仿函式，呼叫時，如果傳回 true 只是它的引數測試為 false。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函式引數的類型。|
|delegate_type|泛型委派類型。|
|result_type|仿函式結果的型別。|

|成員|描述|
|------------|-----------------|
|logical_not|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述單一引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 如果其引數會測試為 false。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or"></a> logical_or (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 的第一個引數或第二個測試，做為 true 時，才。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|logical_or|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數或做為第二個測試為 true。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus"></a> 減號 (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回第一個引數減去第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數和傳回值類型。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|minus|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回第一個引數減去第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus"></a> 模數 (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回第一個引數，第二個模數。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數和傳回值類型。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|模數|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回第一個引數，第二個模數。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies"></a> 乘以 (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回第二個時間的第一個引數。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數和傳回值類型。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|multiplies|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回第二個時間的第一個引數。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate"></a> negate (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回否定其引數。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函式引數的類型。|
|delegate_type|泛型委派類型。|
|result_type|仿函式結果的型別。|

|成員|描述|
|------------|-----------------|
|negate|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述單一引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回否定其引數。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to"></a> not_equal_to (STL/CLR)

此範本類別描述仿函式，呼叫時，則傳回 true 只有第一個引數不是等於第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|not_equal_to|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它只會傳回 true 的第一個引數是否不等於第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1"></a> not1 (STL/CLR)

會產生`unary_negate`的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>範本參數

*樂趣*<br/>
仿函式的型別。

#### <a name="function-parameters"></a>函式參數

*仿函式*<br/>
包裝函式。

### <a name="remarks"></a>備註

範本函式會傳回[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`。 您可以使用它作為便利的方式來將單一引數的仿函式包裝在仿函數時，提供其邏輯 NOT。

### <a name="example"></a>範例

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2"></a> not2 (STL/CLR)

會產生`binary_negate`的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>範本參數

*樂趣*<br/>
仿函式的型別。

#### <a name="function-parameters"></a>函式參數

*仿函式*<br/>
包裝函式。

### <a name="remarks"></a>備註

範本函式會傳回[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`。 您可以使用它作為便利的方式來將兩個引數的仿函式包裝在仿函數時，提供其邏輯 NOT。

### <a name="example"></a>範例

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus"></a> 再加上 (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回第一個引數再加上第二個。 您在使用指定的函式物件，其引數類型方面。

### <a name="syntax"></a>語法

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數和傳回值類型。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派類型。|
|first_argument_type|仿函式的第一個引數型別。|
|result_type|仿函式結果的型別。|
|second_argument_type|仿函式的第二個引數的類型。|

|成員|描述|
|------------|-----------------|
|plus|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|運算子 delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回第一個引數再加上第二個。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate"></a> unary_delegate (STL/CLR)

Genereic 類別描述單一引數的委派。 您在使用指定的委派，根據其引數和傳回類型。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數型別。

*結果*<br/>
傳回型別。

### <a name="remarks"></a>備註

Genereic 委派描述單一引數的函式。

請注意，針對：

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

型別`Fun1`和`Fun2`是同義字，而為：

`delegate int Fun1(int);`

`delegate int Fun2(int);`

它們不是相同的型別。

### <a name="example"></a>範例

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn (STL/CLR)

Genereic 類別描述單一引數的委派，會傳回**void**。 您在使用指定的委派，根據其引數型別。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>參數

*引數*<br/>
引數型別。

### <a name="remarks"></a>備註

Genereic 委派描述單一引數函式會傳回**void**。

請注意，針對：

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

型別`Fun1`和`Fun2`是同義字，而為：

`delegate void Fun1(int);`

`delegate void Fun2(int);`

它們不是相同的型別。

### <a name="example"></a>範例

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate"></a> unary_negate (STL/CLR)

此範本類別描述仿函式，呼叫時，會傳回邏輯不是其預存的單一引數函式。 您在使用指定的函式物件，根據其預存的仿函式。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>參數

*樂趣*<br/>
預存的仿函式的型別。

### <a name="member-functions"></a>成員函式

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函式引數的類型。|
|delegate_type|泛型委派類型。|
|result_type|仿函式結果的型別。|

|成員|描述|
|------------|-----------------|
|unary_negate|建構函式。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函式。|
|delegate_type ^|將轉換成委派仿函式。|

### <a name="remarks"></a>備註

此範本類別描述單一引數仿函數時，會儲存其他單一引數的仿函式。 它會定義此成員運算子`operator()`這麼一來，該物件為函式呼叫時，它會傳回邏輯不是預存的仿函式呼叫的引數。

您也可以將物件傳遞為函式引數型別是`delegate_type^`並會適當地加以轉換。

### <a name="example"></a>範例

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```
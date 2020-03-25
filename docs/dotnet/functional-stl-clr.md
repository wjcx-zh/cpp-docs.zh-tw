---
title: functional (STL/CLR)
ms.date: 11/04/2016
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
ms.openlocfilehash: 2d06a92fea9a702633216e3244879687b66f97d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208724"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

包含 STL/CLR 標頭 `<cliext/functional>`，以定義多個範本類別和相關的範本委派和函式。

## <a name="syntax"></a>語法

```
#include <functional>
```

## <a name="requirements"></a>需求

**標頭：** \<cliext/功能性 >

**命名空間：** cliext

## <a name="declarations"></a>宣告

|委派|描述|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|雙引數委派。|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|傳回**void**的雙引數委派。|
|[unary_delegate (STL/CLR)](#unary_delegate)|一個引數委派。|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|傳回**void**的一個引數委派。|

|類別|描述|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|仿函數，以否定兩個引數的仿函數。|
|[binder1st (STL/CLR)](#binder1st)|仿函數，以將第一個引數系結至兩個引數仿函數。|
|[binder2nd (STL/CLR)](#binder2nd)|仿函數，以將第二個引數系結至兩個引數仿函數。|
|[divides (STL/CLR)](#divides)|除仿函數。|
|[equal_to (STL/CLR)](#equal_to)|相等比較仿函數。|
|[greater (STL/CLR)](#greater)|較大的比較仿函數。|
|[greater_equal (STL/CLR)](#greater_equal)|較大或相等的比較仿函數。|
|[less (STL/CLR)](#less)|較少的比較仿函數。|
|[less_equal (STL/CLR)](#less_equal)|小於或等於比較仿函數。|
|[logical_and (STL/CLR)](#logical_and)|邏輯 AND 仿函數。|
|[logical_not (STL/CLR)](#logical_not)|邏輯 NOT 仿函數。|
|[logical_or (STL/CLR)](#logical_or)|Logical 或仿函數。|
|[minus (STL/CLR)](#minus)|減去仿函數。|
|[modulus (STL/CLR)](#modulus)|模數仿函數。|
|[multiplies (STL/CLR)](#multiplies)|將仿函數相乘。|
|[negate (STL/CLR)](#negate)|仿函數會傳回其引數否定。|
|[not_equal_to (STL/CLR)](#not_equal_to)|不等於比較仿函數。|
|[plus (STL/CLR)](#plus)|新增仿函數。|
|[unary_negate (STL/CLR)](#unary_negate)|仿函數會否定一個引數仿函數。|

|函式|描述|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|產生引數和仿函數的 binder1st。|
|[bind2nd (STL/CLR)](#bind2nd)|產生引數和仿函數的 binder2nd。|
|[not1 (STL/CLR)](#not1)|產生仿函數的 unary_negate。|
|[not2 (STL/CLR)](#not2)|產生仿函數的 binary_negate。|

## <a name="members"></a>成員

## <a name="binary_delegate-stlclr"></a><a name="binary_delegate"></a>binary_delegate （STL/CLR）

Genereic 類別描述兩個引數的委派。 您可以使用它在其引數和傳回類型方面指定委派。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>參數

*Arg1*<br/>
第一個引數的類型。

*Arg2*<br/>
第二個引數的類型。

*結果*<br/>
傳回類型。

### <a name="remarks"></a>備註

Genereic 委派描述兩個引數的函數。

請注意，針對：

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

`Fun1` 和 `Fun2` 的類型是同義字，而適用于：

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

它們的類型不同。

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

## <a name="binary_delegate_noreturn-stlclr"></a><a name="binary_delegate_noreturn"></a>binary_delegate_noreturn （STL/CLR）

Genereic 類別描述會傳回**void**的雙引數委派。 您可以使用它在其引數的角度指定委派。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>參數

*Arg1*<br/>
第一個引數的類型。

*Arg2*<br/>
第二個引數的類型。

### <a name="remarks"></a>備註

Genereic 委派描述會傳回**void**的雙引數函數。

請注意，針對：

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

`Fun1` 和 `Fun2` 的類型是同義字，而適用于：

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

它們的類型不同。

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

## <a name="binary_negate-stlclr"></a><a name="binary_negate"></a>binary_negate （STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回其儲存的雙引數仿函數的邏輯 NOT。 您可以使用它在其預存仿函數的角度指定函式物件。

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

*節日*<br/>
預存仿函數的類型。

## <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|
|stored_function_type|仿函數的類型。|

|member|描述|
|------------|-----------------|
|binary_negate|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^ （）|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述儲存另一個兩個引數仿函數的雙引數仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回以兩個引數呼叫之預存仿函數的邏輯 NOT。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="bind1st-stlclr"></a><a name="bind1st"></a>bind1st （STL/CLR）

產生引數和仿函數的 `binder1st`。

### <a name="syntax"></a>語法

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>範本參數

*Arg*<br/>
引數型別。

*節日*<br/>
仿函數的類型。

#### <a name="function-parameters"></a>函數參數

*仿函數*<br/>
要包裝的仿函數。

*left*<br/>
要換行的第一個引數。

### <a name="remarks"></a>備註

此範本函式會傳回[binder1st （STL/CLR）](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`。 在以第二個引數呼叫它的單一引數仿函數中，您可以使用它來將兩個引數仿函數和其第一個引數換行。

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

## <a name="bind2nd-stlclr"></a><a name="bind2nd"></a>bind2nd （STL/CLR）

產生引數和仿函數的 `binder2nd`。

### <a name="syntax"></a>語法

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>範本參數

*Arg*<br/>
引數型別。

*節日*<br/>
仿函數的類型。

#### <a name="function-parameters"></a>函數參數

*仿函數*<br/>
要包裝的仿函數。

*right*<br/>
要換行的第二個引數。

### <a name="remarks"></a>備註

此範本函式會傳回[binder2nd （STL/CLR）](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`。 您可以使用它，在以第一個引數呼叫它的單一引數仿函數中，將兩個引數的仿函數和其第二個引數換行。

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

## <a name="binder1st-stlclr"></a><a name="binder1st"></a>binder1st （STL/CLR）

此樣板類別描述一個引數仿函數，當呼叫它時，會傳回其預存的雙引數仿函數，其名為，其儲存的第一個引數和所提供的第二個引數。 您可以使用它在其預存仿函數的角度指定函式物件。

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

*節日*<br/>
預存仿函數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|
|stored_function_type|仿函數的類型。|

|member|描述|
|------------|-----------------|
|binder1st|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^ （）|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此樣板類別描述單一引數仿函數，其中儲存兩個引數的仿函數和第一個引數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回使用預存的第一個引數和所提供的第二個引數呼叫預存仿函數的結果。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="binder2nd-stlclr"></a><a name="binder2nd"></a>binder2nd （STL/CLR）

此樣板類別描述一個引數仿函數，呼叫時，會傳回其預存的雙引數仿函數，並以提供的第一個引數和其儲存的第二個引數呼叫。 您可以使用它在其預存仿函數的角度指定函式物件。

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

*節日*<br/>
預存仿函數的類型。

## <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|
|stored_function_type|仿函數的類型。|

|member|描述|
|------------|-----------------|
|binder2nd|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^ （）|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此樣板類別描述單一引數仿函數，其中儲存兩個引數的仿函數和第二個引數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回以提供的第一個引數和儲存的第二個引數呼叫預存仿函數的結果。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="divides-stlclr"></a><a name="divides"></a>除法（STL/CLR）

此樣板類別描述一個仿函數，當呼叫此方法時，會傳回第一個引數除以第二個。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數和傳回值的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|divides|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^ （）|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回第一個引數除以第二個。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="equal_to-stlclr"></a><a name="equal_to"></a>equal_to （STL/CLR）

此樣板類別描述的仿函數，在呼叫時，只有在第一個引數等於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|equal_to|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^ （）|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當呼叫物件當做函式時，只有當第一個引數等於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="greater-stlclr"></a><a name="greater"></a>大於（STL/CLR）

此樣板類別描述的仿函數，在呼叫時，只有在第一個引數大於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|greater|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當呼叫物件當做函式時，只有當第一個引數大於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="greater_equal-stlclr"></a><a name="greater_equal"></a>greater_equal （STL/CLR）

此樣板類別描述的仿函數，在呼叫時，只有在第一個引數大於或等於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|greater_equal|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，只有當第一個引數大於或等於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="less-stlclr"></a><a name="less"></a>less （STL/CLR）

此樣板類別描述一個仿函數，在呼叫時，只有在第一個引數小於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|less|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當呼叫物件當做函式時，只有當第一個引數小於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="less_equal-stlclr"></a><a name="less_equal"></a>less_equal （STL/CLR）

此樣板類別描述的仿函數，在呼叫時，只有在第一個引數小於或等於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|less_equal|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，只有當第一個引數小於或等於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="logical_and-stlclr"></a><a name="logical_and"></a>logical_and （STL/CLR）

此樣板類別描述一個仿函數，在呼叫時，只有在第一個引數和第二個測試為 true 時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|logical_and|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當呼叫物件當做函式時，只有在第一個引數和第二個測試為 true 時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="logical_not-stlclr"></a><a name="logical_not"></a>logical_not （STL/CLR）

此樣板類別描述一個仿函數，呼叫時，只有在其引數測試為 false 時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函數引數的類型。|
|delegate_type|泛型委派的類型。|
|result_type|仿函數結果的類型。|

|member|描述|
|------------|-----------------|
|logical_not|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述一個引數仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，只有在其引數測試為 false 時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="logical_or-stlclr"></a><a name="logical_or"></a>logical_or （STL/CLR）

此樣板類別描述一個仿函數，在呼叫時，只有在第一個引數或第二個測試為 true 時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|logical_or|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當呼叫物件當做函式時，只有在第一個引數或第二個測試為 true 時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="minus-stlclr"></a><a name="minus"></a>減號（STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回第一個引數減去第二個。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數和傳回值的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|減|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回第一個引數減去第二個。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="modulus-stlclr"></a><a name="modulus"></a>模數（STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回第一個引數模數第二個。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數和傳回值的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|模數|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回第一個引數模數第二個。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="multiplies-stlclr"></a><a name="multiplies"></a>乘法（STL/CLR）

此樣板類別描述的仿函數，在呼叫時，會傳回第二個引數次。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數和傳回值的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|multiplies|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回第二個引數次。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="negate-stlclr"></a><a name="negate"></a>否定（STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回其引數否定。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函數引數的類型。|
|delegate_type|泛型委派的類型。|
|result_type|仿函數結果的類型。|

|member|描述|
|------------|-----------------|
|negate|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述一個引數仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回其引數否定。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="not_equal_to-stlclr"></a><a name="not_equal_to"></a>not_equal_to （STL/CLR）

此樣板類別描述一個仿函數，在呼叫時，只有在第一個引數不等於第二個時，才會傳回 true。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|not_equal_to|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，只有在第一個引數不等於第二個時，才會傳回 true。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="not1-stlclr"></a><a name="not1"></a>not1 （STL/CLR）

產生仿函數的 `unary_negate`。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>範本參數

*節日*<br/>
仿函數的類型。

#### <a name="function-parameters"></a>函數參數

*仿函數*<br/>
要包裝的仿函數。

### <a name="remarks"></a>備註

此範本函式會傳回[unary_negate （STL/CLR）](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`。 在提供邏輯 NOT 的仿函數中，您可以使用它來將單一引數仿函數換行。

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

## <a name="not2-stlclr"></a><a name="not2"></a>not2 （STL/CLR）

產生仿函數的 `binary_negate`。

### <a name="syntax"></a>語法

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>範本參數

*節日*<br/>
仿函數的類型。

#### <a name="function-parameters"></a>函數參數

*仿函數*<br/>
要包裝的仿函數。

### <a name="remarks"></a>備註

此範本函式會傳回[binary_negate （STL/CLR）](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`。 您可以使用它，在傳遞其邏輯 NOT 的仿函數中，將兩個引數仿函數換行。

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

## <a name="plus-stlclr"></a><a name="plus"></a>plus （STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回第一個引數加上第二個。 您可以使用它的引數類型來指定函式物件。

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

*Arg*<br/>
引數和傳回值的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|delegate_type|泛型委派的類型。|
|first_argument_type|仿函數第一個引數的類型。|
|result_type|仿函數結果的類型。|
|second_argument_type|仿函數第二個引數的類型。|

|member|描述|
|------------|-----------------|
|加|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|運算子 delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述兩個引數的仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回第一個引數加上第二個。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

## <a name="unary_delegate-stlclr"></a><a name="unary_delegate"></a>unary_delegate （STL/CLR）

Genereic 類別描述一個引數委派。 您可以使用它在其引數和傳回類型方面指定委派。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>參數

*Arg*<br/>
引數型別。

*結果*<br/>
傳回類型。

### <a name="remarks"></a>備註

Genereic 委派描述一個引數函式。

請注意，針對：

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

`Fun1` 和 `Fun2` 的類型是同義字，而適用于：

`delegate int Fun1(int);`

`delegate int Fun2(int);`

它們的類型不同。

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

## <a name="unary_delegate_noreturn-stlclr"></a><a name="unary_delegate_noreturn"></a>unary_delegate_noreturn （STL/CLR）

Genereic 類別描述會傳回**void**的單一引數委派。 您可以使用它在其引數類型的角度指定委派。

### <a name="syntax"></a>語法

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>參數

*Arg*<br/>
引數型別。

### <a name="remarks"></a>備註

Genereic 委派描述一個會傳回**void**的引數函式。

請注意，針對：

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

`Fun1` 和 `Fun2` 的類型是同義字，而適用于：

`delegate void Fun1(int);`

`delegate void Fun2(int);`

它們的類型不同。

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

## <a name="unary_negate-stlclr"></a><a name="unary_negate"></a>unary_negate （STL/CLR）

此樣板類別描述一個仿函數，當呼叫它時，會傳回其儲存的單一引數仿函數的邏輯 NOT。 您可以使用它在其預存仿函數的角度指定函式物件。

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

*節日*<br/>
預存仿函數的類型。

### <a name="member-functions"></a>成員函數

|類型定義|描述|
|---------------------|-----------------|
|argument_type|仿函數引數的類型。|
|delegate_type|泛型委派的類型。|
|result_type|仿函數結果的類型。|

|member|描述|
|------------|-----------------|
|unary_negate|結構仿函數。|

|運算子|描述|
|--------------|-----------------|
|operator()|計算所需的函數。|
|delegate_type ^|將仿函數轉換成委派。|

### <a name="remarks"></a>備註

此範本類別描述儲存另一個引數仿函數的單一引數仿函數。 它會定義成員運算子 `operator()` 因此，當物件被呼叫為函式時，它會傳回以引數呼叫之儲存仿函數的邏輯 NOT。

您也可以將物件當做函式引數傳遞，其型別為 `delegate_type^` 而且會適當地轉換。

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

---
title: '&lt;functional&gt; 函式 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::bind
- xfunctional/std::bind1st
- xfunctional/std::bind2nd
- xfunctional/std::bit_and
- xfunctional/std::bit_not
- xfunctional/std::bit_or
- xfunctional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- xfunctional/std::mem_fn
- xfunctional/std::mem_fun_ref
- xfunctional/std::not1
- xfunctional/std::not2
- xfunctional/std::ptr_fun
- functional/std::ref
- functional/std::swap
dev_langs:
- C++
helpviewer_keywords:
- std::bind [C++]
- std::bind1st
- std::bind2nd
- std::bit_and [C++]
- std::bit_not [C++]
- std::bit_or [C++]
- std::bit_xor [C++]
- std::cref [C++]
ms.assetid: c34d0b45-50a7-447a-9368-2210d06339a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a2b776fb155d8927b610de38bdd79370f4c0803
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39208646"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; 函式

||||
|-|-|-|
|[bind](#bind)|[bind1st](#bind1st)|[bind2nd](#bind2nd)|
|[bit_and](#bit_and)|[bit_not](#bit_not)|[bit_or](#bit_or)|
|[bit_xor](#bit_xor)|[cref](#cref)|[mem_fn](#mem_fn)|
|[mem_fun](#mem_fun)|[mem_fun_ref](#mem_fun_ref)|[not1](#not1)|
|[not2](#not2)|[ptr_fun](#ptr_fun)|[ref](#ref)|
|[swap](#swap)|

## <a name="bind"></a>  bind

將引數繫結至可呼叫物件。

```cpp
template <class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);

template <class Ret, class Fty, class T1, class T2, ..., class TN>
unspecified bind(Fty fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>參數

*Fty*要呼叫的物件類型。

*TN*第 n 個呼叫引數的類型。

*fn*来呼叫的物件。

*tN*第 n 個呼叫引數。

### <a name="remarks"></a>備註

`Fty, T1, T2, ..., TN` 類型必須是複製建構，且對於 `w1, w2, ..., wN` 某些值來說，`INVOKE(fn, t1, ..., tN)` 必須是有效的運算式。

第一個範本函式會傳回含弱式結果類型的轉送呼叫包裝函式 `g`。 效果`g(u1, u2, ..., uM)`已`INVOKE(f, v1, v2, ..., vN, ` [result_of](../standard-library/result-of-class.md)`<Fty cv (V1, V2, ..., VN)>::type)`，其中`cv`是 cv 限定詞`g`的值和類型的繫結的引數`v1, v2, ..., vN`判定為以下指定。 您可以使用它將引數繫結至可呼叫的物件，以利用量身訂做的引數清單來製作可呼叫物件。

第二個範本函式會傳回含 `result_type` 巢狀類型的轉送呼叫包裝函式 `g`，該類型與 `Ret` 同義。 `g(u1, u2, ..., uM)` 的效果為 `INVOKE(f, v1, v2, ..., vN, Ret)`，其中 `cv` 是 `g` 的 cv 限定詞，而繫結引數 `v1, v2, ..., vN` 的值和類型則依下列指定方式來判斷。 您可以使用它將引數繫結至可呼叫的物件，以利用量身訂做的引數清單和指定的傳回類型，來製作可呼叫物件。

繫結引數 `v1, v2, ..., vN` 的值及其對應的 `V1, V2, ..., VN` 類型，取決於對 `bind` 與呼叫包裝函式 `g` cv 限定詞 `cv` 的呼叫中，`Ti` 類型的對應引數類型 `ti`，如下所示：

如果 `ti` 是 `reference_wrapper<T>` 類型，`vi` 引數即為 `ti.get()`，而其 `Vi` 類型為 `T&`；

如果值`std::is_bind_expression<Ti>::value`已 **，則為 true**引數`vi`是`ti(u1, u2, ..., uM)`及其類型`Vi`是`result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type`;

如果 `std::is_placeholder<Ti>::value` 的 `j` 值不是零，`vi` 引數即為 `uj`，而其 `Vi` 類型為 `Uj&`；

否則，引數 `vi` 是 `ti`，而其 `Vi` 類型為 `Ti` `cv` `&`。

例如，假設以 `f(int, int)` 函式來看，運算式 `bind(f, _1, 0)` 會傳回轉送呼叫包裝函式 `cw`，以讓 `cw(x)` 呼叫 `f(x, 0)`。 運算式 `bind(f, 0, _1)` 會傳回轉送呼叫包裝函式`cw`，以讓 `cw(x)` 呼叫 `f(0, x)`。

除了引數 `fn` 以外，呼叫 `bind` 的引數數目必須等於可以傳遞至可呼叫物件 `fn` 的引數數目。 因此，`bind(cos, 1.0)` 為正確，而 `bind(cos)` 和 `bind(cos, _1, 0.0)` 不正確。

針對呼叫 `bind` 的所有預留位置引數，在呼叫包裝函式的函數呼叫中，由 `bind` 所傳回的引數數目必須至少與最大編號的 `is_placeholder<PH>::value` 值一樣大。 因此，`bind(cos, _2)(0.0, 1.0)` 為正確 (並傳回 `cos(1.0)`)，而 `bind(cos, _2)(0.0)` 不正確。

### <a name="example"></a>範例

```cpp
// std__functional__bind.cpp
// compile with: /EHsc
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std::placeholders;

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

void product(double x, double y)
{
    std::cout << x << "*" << y << " == " << x * y << std::endl;
}

int main()
{
    double arg[] = { 1, 2, 3 };

    std::for_each(&arg[0], arg + 3, square);
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(product, _1, 2));
    std::cout << std::endl;

    std::for_each(&arg[0], arg + 3, std::bind(square, _1));

    return (0);
}

```

```Output
1^2 == 1
2^2 == 4
3^2 == 9

1*2 == 2
2*2 == 4
3*2 == 6

1^2 == 1
2^2 == 4
3^2 == 9
```

## <a name="bind1st"></a>  bind1st

協助程式樣板函式，可建立配接器，透過將二元函式的第一個引數繫結至指定值，將二元函式物件轉換成一元函式物件。

```cpp
template <class Operation, class Type>
binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>參數

*func*二元函式物件轉換成一元函式物件。

*左*二元函式物件的第一個引數所繫結的值。

### <a name="return-value"></a>傳回值

一元函式物件所產生的繫結至值的二元函式物件的第一個引數*左*。

### <a name="remarks"></a>備註

函式繫結器是一種函式配接器，其會傳回函式物件，因此可用於特定類型的函式組合，以建構更複雜且強大的運算式。

如果*func*是類型的物件`Operation`並`c`是常數，則`bind1st`( `func`， `c`) 相當於[binder1st](../standard-library/binder1st-class.md)類別建構函式`binder1st` <  `Operation`> ( `func`， `c`) 而且更方便。

### <a name="example"></a>範例

```cpp
// functional_bind1st.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan5: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 5);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind1st(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare: counting the number of integers > 5 in the vector
    // with a user defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan5());
    cout << "The number of elements in v1 greater than 5 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind2nd(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 5 is: 4.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bind2nd"></a>  bind2nd

協助程式樣板函式，可建立配接器，透過將二元函式的第二個引數繫結至指定值，將二元函式物件轉換成一元函式物件。

```cpp
template <class Operation, class Type>
binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>參數

*func*二元函式物件轉換成一元函式物件。

*右*二元函式物件的第二個引數所繫結的值。

### <a name="return-value"></a>傳回值

一元函式物件所產生的繫結至值的二元函式物件的第二個引數*右*。

### <a name="remarks"></a>備註

函式繫結器是一種函式配接器，其會傳回函式物件，因此可用於特定類型的函式組合，以建構更複雜且強大的運算式。

如果*func*是類型的物件`Operation`並`c`是常數，則`bind2nd`( `func`， `c` ) 相當於[binder2nd](../standard-library/binder2nd-class.md)類別建構函式**binder2nd\<作業 >** ( `func`， `c` )、 更方便。

### <a name="example"></a>範例

```cpp
// functional_bind2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

// Creation of a user-defined function object
// that inherits from the unary_function base class
class greaterthan15: unary_function<int, bool>
{
public:
    result_type operator()(argument_type i)
    {
        return (result_type)(i > 15);
    }
};

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1a;
    result1a = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1a << "." << endl;

    // Compare counting the number of integers > 15 in the vector
    // with a user-defined function object
    vector<int>::iterator::difference_type result1b;
    result1b = count_if(v1.begin(), v1.end(), greaterthan15());
    cout << "The number of elements in v1 greater than 15 is: "
         << result1b << "." << endl;

    // Count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(), bind1st(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 greater than 15 is: 2.
The number of elements in v1 less than 10 is: 2.
```

## <a name="bit_and"></a>  bit_and

在其引數執行位元 AND 運算 (二元 `operator&`) 的預先定義函式物件。

```cpp
template <class Type = void>
struct bit_and : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
 };

// specialized transparent functor for operator&
template <>
struct bit_and<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const  ->
        decltype(std::forward<T>(Left) & std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*支援任何型別`operator&`會指定或推斷類型的運算元。

*左*位元的 AND 運算的左的運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*右*位元的 AND 運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

### <a name="return-value"></a>傳回值

`Left & Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator&` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_and` 仿函數僅限於整數類型，或會實作二元 `operator&` 的使用者定義類型。

## <a name="bit_not"></a>  bit_not

在其引數執行位元補數 (NOT) 運算 (一元 `operator~`) 的預先定義函式物件。

```cpp
template <class Type = void>
struct bit_not : public unary_function<Type, Type>
 {
    Type operator()(const Type& Right) const;
 };

// specialized transparent functor for operator~
template <>
struct bit_not<void>
 {
    template <class Type>
    auto operator()(Type&& Right) const  ->  decltype(~std::forward<Type>(Right));
 };
```

### <a name="parameters"></a>參數

*型別*支援的一元 （unary） 的型別`operator~`。

*右*位元補數運算的運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送 lvalue 或 rvalue 參考類型的引數推斷*型別*。

### <a name="return-value"></a>傳回值

`~ Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator~` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_not` 仿函數僅限於整數類型，或會實作二元 `operator~` 的使用者定義類型。

## <a name="bit_or"></a>  bit_or

在其引數執行位元 OR 運算 (`operator|`) 的預先定義函式物件。

```cpp
template <class Type = void>
struct bit_or : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
 };

// specialized transparent functor for operator|
template <>
struct bit_or<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        ->  decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*支援任何型別`operator|`會指定或推斷類型的運算元。

*左*位元 OR 運算的左的運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*右*位元 OR 運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

### <a name="return-value"></a>傳回值

`Left | Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator|` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_or` 函式僅限於整數類型，或會實作 `operator|` 的使用者定義類型。

## <a name="bit_xor"></a>  bit_xor

在其引數執行位元 XOR 運算 (二元 `operator^`) 的預先定義函式物件。

```cpp
template <class Type = void>
struct bit_xor : public binary_function<Type, Type, Type> {
    Type operator()(
    const Type& Left,
    const Type& Right) const;
 };

// specialized transparent functor for operator^
template <>
struct bit_xor<void>
{
    template <class T, class U>
    auto operator()(T&& Left, U&& Right) const
        -> decltype(std::forward<T>(Left) ^ std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*型別*， *T*， *U*支援任何型別`operator^`會指定或推斷類型的運算元。

*左*位元 XOR 運算的左的運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*T*。

*右*位元 XOR 運算的右運算元。 特製化的樣板採用類型的左值參考引數*型別*。 此特製化的範本會完美地轉送的左值和右值參考引數推斷型別*U*。

### <a name="return-value"></a>傳回值

`Left ^ Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator^` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_xor` 仿函數僅限於整數類型，或會實作二元 `operator^` 的使用者定義類型。

## <a name="cref"></a>  cref

從引數建構常數`reference_wrapper`。

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>參數

*Ty*包裝的引數的類型。

*arg*包裝的引數。

### <a name="remarks"></a>備註

第一個函式會傳回 `reference_wrapper<const Ty>(arg.get())`。 您可以使用此項目，來包裝 const 參考。 第二個函式會傳回 `reference_wrapper<const Ty>(arg)`。 您可以使用此項目，將已包裝的參考重新包裝為 const 參考。

### <a name="example"></a>範例

```cpp
// std__functional__cref.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    int i = 1;

    std::cout << "i = " << i << std::endl;
    std::cout << "cref(i) = " << std::cref(i) << std::endl;
    std::cout << "cref(neg)(i) = "
        << std::cref(&neg)(i) << std::endl;

    return (0);
    }

```

```Output
i = 1
cref(i) = 1
cref(neg)(i) = -1
```

## <a name="mem_fn"></a>  mem_fn

產生簡單呼叫包裝函式。

```cpp
template <class Ret, class Ty>
unspecified mem_fn(Ret Ty::*pm);
```

### <a name="parameters"></a>參數

*Ret*包裝函式的傳回型別。

*Ty*成員函式指標的類型。

### <a name="remarks"></a>備註

範本函式會傳回含弱式結果類型的簡單呼叫包裝函式 `cw`，以讓運算式 `cw(t, a2, ..., aN)` 相當於 `INVOKE(pm, t, a2, ..., aN)`。 它不會擲回任何例外狀況。

傳回的呼叫包裝函式衍生自`std::unary_function<cv Ty*, Ret>`(進而定義巢狀的類型`result_type`同義*Ret*和巢狀型別`argument_type`同義`cv Ty*`) 只有當類型*Ty*是使用 cv 限定詞的成員函式的指標`cv`採用任何引數。

傳回的呼叫包裝函式衍生自`std::binary_function<cv Ty*, T2, Ret>`(進而定義巢狀的類型`result_type`同義*Ret*，則巢狀類型`first argument_type`同義`cv Ty*`，以及巢狀的類型`second argument_type`的同義字`T2`) 只有當型別*Ty*是使用 cv 限定詞的成員函式的指標`cv`採用一個引數的型別`T2`。

### <a name="example"></a>範例

```cpp
// std__functional__mem_fn.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

class Funs
    {
public:
    void square(double x)
        {
        std::cout << x << "^2 == " << x * x << std::endl;
        }

    void product(double x, double y)
        {
        std::cout << x << "*" << y << " == " << x * y << std::endl;
        }
    };

int main()
    {
    Funs funs;

    std::mem_fn(&Funs::square)(funs, 3.0);
    std::mem_fn(&Funs::product)(funs, 3.0, 2.0);

    return (0);
    }

```

```Output
3^2 == 9
3*2 == 6
```

## <a name="mem_fun"></a>  mem_fun

協助程式樣板函式，可用來建構使用指標引數初始化時之成員函式的物件配接器。

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pmem)(Arg) const);
```

### <a name="parameters"></a>參數

*pmem*類別的成員函式的指標`Type`轉換成函式物件。

### <a name="return-value"></a>傳回值

類型為 `mem_fun_t` 或 `mem_fun1_t` 的 **const** 或 **non_const** 函式物件。

### <a name="example"></a>範例

```cpp
// functional_mem_fun.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class StoreVals
{
    int val;
public:
    StoreVals() { val = 0; }
    StoreVals(int j) { val = j; }

    bool display() { cout << val << " "; return true; }
    int squareval() { val *= val; return val; }
    int lessconst(int k) {val -= k; return val; }
};

int main( )
{
    vector<StoreVals *> v1;

    StoreVals sv1(5);
    v1.push_back(&sv1);
    StoreVals sv2(10);
    v1.push_back(&sv2);
    StoreVals sv3(15);
    v1.push_back(&sv3);
    StoreVals sv4(20);
    v1.push_back(&sv4);
    StoreVals sv5(25);
    v1.push_back(&sv5);

    cout << "The original values stored are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun calling member function through a pointer
    // square each value in the vector using squareval ()
    for_each(v1.begin(), v1.end(), mem_fun<int, StoreVals>(&StoreVals::squareval));
    cout << "The squared values are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;

    // Use of mem_fun1 calling member function through a pointer
    // subtract 5 from each value in the vector using lessconst ()
    for_each(v1.begin(), v1.end(),
        bind2nd (mem_fun1<int, StoreVals,int>(&StoreVals::lessconst), 5));
    cout << "The squared values less 5 are: " ;
    for_each(v1.begin(), v1.end(), mem_fun<bool, StoreVals>(&StoreVals::display));
    cout << endl;
}
```

## <a name="mem_fun_ref"></a>  mem_fun_ref

Helper 範本函式，用以在使用參考引數初始化時建構成員函式的物件配接器。

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pmem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pmem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pmem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pmem)(Arg) const);
```

### <a name="parameters"></a>參數

*pmem*類別的成員函式的指標`Type`轉換成函式物件。

### <a name="return-value"></a>傳回值

A **const**或是`non_const`函式物件的型別`mem_fun_ref_t`或`mem_fun1_ref_t`。

### <a name="example"></a>範例

```cpp
// functional_mem_fun_ref.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

class NumVals
   {
   int val;
   public:
   NumVals ( ) { val = 0; }
   NumVals ( int j ) { val = j; }

   bool display ( ) { cout << val << " "; return true; }
   bool isEven ( ) { return ( bool )  !( val %2 ); }
   bool isPrime( )
   {
      if (val < 2) { return true; }
      for (int i = 2; i <= val / i; ++i)
      {
         if (val % i == 0) { return false; }
      }
      return true;
   }
};

int main( )
{
   vector <NumVals> v1 ( 13 ), v2 ( 13 );
   vector <NumVals>::iterator v1_Iter, v2_Iter;
   int i, k;

   for ( i = 0; i < 13; i++ ) v1 [ i ] = NumVals ( i+1 );
   for ( k = 0; k < 13; k++ ) v2 [ k ] = NumVals ( k+1 );

   cout << "The original values stored in v1 are: " ;
   for_each( v1.begin( ), v1.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the primes in the vector using isPrime ( )
   v1_Iter = remove_if ( v1.begin( ),  v1.end( ),
      mem_fun_ref ( &NumVals::isPrime ) );
   cout << "With the primes removed, the remaining values in v1 are: " ;
   for_each( v1.begin( ), v1_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   cout << "The original values stored in v2 are: " ;
   for_each( v2.begin( ), v2.end( ),
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;

   // Use of mem_fun_ref calling member function through a reference
   // remove the even numbers in the vector v2 using isEven ( )
   v2_Iter = remove_if ( v2.begin( ),  v2.end( ),
      mem_fun_ref ( &NumVals::isEven ) );
   cout << "With the even numbers removed, the remaining values are: " ;
   for_each( v2.begin( ),  v2_Iter,
   mem_fun_ref ( &NumVals::display ) );
   cout << endl;
}
```

```Output
The original values stored in v1 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the primes removed, the remaining values in v1 are: 4 6 8 9 10 12
The original values stored in v2 are: 1 2 3 4 5 6 7 8 9 10 11 12 13
With the even numbers removed, the remaining values are: 1 3 5 7 9 11 13
```

## <a name="not1"></a>  not1

傳回一元述詞的補數。

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& pred);
```

### <a name="parameters"></a>參數

*pred*要變為負值的一元述詞。

### <a name="return-value"></a>傳回值

一元述詞，其為所修改之一元述詞的負值。

### <a name="remarks"></a>備註

如果 `unary_negate` 是建構自 **Pred**( *x*) 一元述詞，則它會傳回 **!Pred**( *x*)。

### <a name="example"></a>範例

```cpp
// functional_not1.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 7; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    // Count the elements greater than 10
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    vector<int>::iterator::difference_type result2;
    // Use the negator to count the elements less than or equal to 10
    result2 = count_if(v1.begin(), v1.end(),
        not1(bind2nd(greater<int>(), 10)));

    cout << "The number of elements in v1 not greater than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 30 35 )
The number of elements in v1 greater than 10 is: 5.
The number of elements in v1 not greater than 10 is: 3.
```

## <a name="not2"></a>  not2

傳回二元述詞的補數。

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>參數

*func*要變為負值的二元述詞。

### <a name="return-value"></a>傳回值

二元述詞，其為所修改之二元述詞的負值。

### <a name="remarks"></a>備註

如果 `binary_negate` 是建構自 **BinPred**( *x*, *y*) 二元述詞，則它會傳回 ! **BinPred**( *x*, *y*)。

### <a name="example"></a>範例

```cpp
// functional_not2.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   v1.push_back( 6262 );
   v1.push_back( 6262 );
   for ( i = 0 ; i < 5 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // use the binary_negate helper function not2
   sort( v1.begin( ), v1.end( ), not2(less<int>( ) ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 6262 6262 41 18467 6334 26500 19169 )
Sorted vector v1 = ( 41 6262 6262 6334 18467 19169 26500 )
Resorted vector v1 = ( 26500 19169 18467 6334 6262 6262 41 )
```

## <a name="ptr_fun"></a>  ptr_fun

Helper 範本函式，可用來將一元和二元函式指標分別轉換成一元和二元可調適性函式。

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>參數

*pfunc*一元或二元函式指標轉換成可調適性函式。

### <a name="return-value"></a>傳回值

第一個範本函式會傳回一元函式[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md) < `Arg`，**結果**> (\* `pfunc`)。

第二個樣板函式會傳回二元函式[pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \< **Arg1**， **Arg2**，**結果**> (\* `pfunc`)。

### <a name="remarks"></a>備註

函式指標是函式物件，可傳遞給需要以參數形式使用函式的任何 C++ 標準程式庫演算法，但它不具可調適性。 若要使用它來搭配配接器 (例如與值繫結或使用它搭配否定運算子)，您必須為其提供能夠進行這類調適的巢狀類型。 由 `ptr_fun` helper 函式進行的一元和二元函式指標轉換，可讓函式配接器使用一元和二元函式指標。

### <a name="example"></a>範例

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a>  ref

從引數建構 `reference_wrapper` 。

```cpp
template <class Ty>
reference_wrapper<Ty> ref(Ty& arg);

template <class Ty>
reference_wrapper<Ty> ref(reference_wrapper<Ty>& arg);
```

### <a name="return-value"></a>傳回值

`arg`的參考，尤其是 `reference_wrapper<Ty>(arg)`。

### <a name="example"></a>範例

下列範例會定義兩個函式：一個繫結至字串變數，另一個繫結至呼叫 `ref`所計算之字串變數的參考。 當變數的值變更時，第一個函式會繼續使用舊的值，第二個函式則使用新的值。

```cpp
#include <algorithm>
#include <functional>
#include <iostream>
#include <iterator>
#include <ostream>
#include <string>
#include <vector>
using namespace std;
using namespace std;
using namespace std::placeholders;

bool shorter_than(const string& l, const string& r) {
    return l.size() < r.size();
}

int main() {
    vector<string> v_original;
    v_original.push_back("tiger");
    v_original.push_back("cat");
    v_original.push_back("lion");
    v_original.push_back("cougar");

    copy(v_original.begin(), v_original.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    string s("meow");

    function<bool (const string&)> f = bind(shorter_than, _1, s);
    function<bool (const string&)> f_ref = bind(shorter_than, _1, ref(s));

    vector<string> v;

    // Remove elements that are shorter than s ("meow")

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Now change the value of s.
    // f_ref, which is bound to ref(s), will use the
    // new value, while f is still bound to the old value.

    s = "kitty";

    // Remove elements that are shorter than "meow" (f is bound to old value of s)

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;

    // Remove elements that are shorter than "kitty" (f_ref is bound to ref(s))

    v = v_original;
    v.erase(remove_if(v.begin(), v.end(), f_ref), v.end());

    copy(v.begin(), v.end(), ostream_iterator<string>(cout, " "));
    cout << endl;
}
```

```Output
tiger cat lion cougar
tiger lion cougar
tiger lion cougar
tiger cougar
```

## <a name="swap"></a>  swap

交換兩個 `function` 物件。

```cpp
template <class Fty>
void swap(function<Fty>& f1, function<Fty>& f2);
```

### <a name="parameters"></a>參數

*Fty*函式物件所控制的類型。

*f1*第一個函式物件。

*f2*第二個函式物件。

### <a name="remarks"></a>備註

函式會傳回 `f1.swap(f2)`。

### <a name="example"></a>範例

```cpp
// std__functional__swap.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "val == " << fn0(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << std::endl;

    swap(fn0, fn1);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }

```

```Output
empty == false
val == -3
empty == true

empty == true
empty == false
val == -3
```

## <a name="see-also"></a>另請參閱

[\<functional>](../standard-library/functional.md)<br/>

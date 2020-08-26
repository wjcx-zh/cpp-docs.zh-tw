---
title: '&lt;functional&gt; 函式'
ms.date: 02/21/2019
f1_keywords:
- functional/std::bind
- functional/std::bind1st
- functional/std::bind2nd
- functional/std::bit_and
- functional/std::bit_not
- functional/std::bit_or
- functional/std::bit_xor
- functional/std::cref
- type_traits/std::cref
- functional/std::mem_fn
- functional/std::mem_fun_ref
- functional/std::not1
- functional/std::not2
- functional/std::not_fn
- functional/std::ptr_fun
- functional/std::ref
- functional/std::swap
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
ms.openlocfilehash: 5e3aa35395c8fd5a42d7127d0b6072a3edf4ace5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838083"
---
# <a name="ltfunctionalgt-functions"></a>&lt;functional&gt; 函式

這些函式在 c + + 11 中已被取代並在 c + + 17 中移除：

[bind1st](#bind1st)\
[bind2nd](#bind2nd)\
[mem_fun](#mem_fun)\
[mem_fun_ref](#mem_fun_ref)\
[ptr_fun](#ptr_fun)

這些函數在 c + + 17 中已被取代：

[not1](#not1)\
[not2](#not2)

## <a name="bind"></a><a name="bind"></a> 綁定

將引數繫結至可呼叫物件。

```cpp
template <class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);

template <class RTy, class FT, class T1, class T2, ..., class TN>
    unspecified bind(FT fn, T1 t1, T2 t2, ..., TN tN);
```

### <a name="parameters"></a>參數

*Fey*\
要呼叫的物件類型。

*Tn*\
第 N 個呼叫引數類型。

*Fn*\
要呼叫的物件。

*Tn*\
第 N 個呼叫引數。

### <a name="remarks"></a>備註

型別 `FT, T1, T2, ..., TN` 必須是複製可建構，而且 `INVOKE(fn, t1, ..., tN)` 必須是適用于某些值的有效運算式 `w1, w2, ..., wN` 。

第一個範本函式會傳回含弱式結果類型的轉送呼叫包裝函式 `g`。 的效果 `g(u1, u2, ..., uM)` 是 `INVOKE(f, v1, v2, ..., vN,` [invoke_result](../standard-library/invoke-result-class.md) `<FT cv (V1, V2, ..., VN)>::type)` ，其中 `cv` 是的 cv 限定詞，而系結 `g` 引數的值和類型則 `v1, v2, ..., vN` 由以下指定。 您可以使用它將引數繫結至可呼叫的物件，以利用量身訂做的引數清單來製作可呼叫物件。

第二個範本函式會傳回含 `result_type` 巢狀類型的轉送呼叫包裝函式 `g`，該類型與 `RTy` 同義。 `g(u1, u2, ..., uM)` 的效果為 `INVOKE(f, v1, v2, ..., vN, RTy)`，其中 `cv` 是 `g` 的 cv 限定詞，而繫結引數 `v1, v2, ..., vN` 的值和類型則依下列指定方式來判斷。 您可以使用它將引數繫結至可呼叫的物件，以利用量身訂做的引數清單和指定的傳回類型，來製作可呼叫物件。

繫結引數 `v1, v2, ..., vN` 的值及其對應的 `V1, V2, ..., VN` 類型，取決於對 `bind` 與呼叫包裝函式 `g` cv 限定詞 `cv` 的呼叫中，`Ti` 類型的對應引數類型 `ti`，如下所示：

如果 `ti` 是 `reference_wrapper<T>` 類型，`vi` 引數即為 `ti.get()`，而其 `Vi` 類型為 `T&`；

如果的值為 `std::is_bind_expression<Ti>::value` **`true`** 引數， `vi` `ti(u1, u2, ..., uM)` 且其類型 `Vi` 為 `result_of<Ti` `cv` `(U1&, U2&, ..., UN&>::type` ;

如果的值 `j` `std::is_placeholder<Ti>::value` 不是零，則引數 `vi` 為 `uj` ，且其類型 `Vi` 為 `Uj&` ;

否則，引數 `vi` 為 `ti` ，且其類型 `Vi` 為 `Ti` `cv` `&` 。

例如，假設以 `f(int, int)` 函式來看，運算式 `bind(f, _1, 0)` 會傳回轉送呼叫包裝函式 `cw`，以讓 `cw(x)` 呼叫 `f(x, 0)`。 運算式 `bind(f, 0, _1)` 會傳回轉送呼叫包裝函式`cw`，以讓 `cw(x)` 呼叫 `f(0, x)`。

呼叫中的引數數目 `bind` 和引數 `fn` 必須等於可傳遞至可呼叫物件的引數數目 `fn` 。 例如， `bind(cos, 1.0)` 是正確的，而且和都不 `bind(cos)` `bind(cos, _1, 0.0)` 正確。

針對呼叫 `bind` 的所有預留位置引數，在呼叫包裝函式的函數呼叫中，由 `bind` 所傳回的引數數目必須至少與最大編號的 `is_placeholder<PH>::value` 值一樣大。 例如， `bind(cos, _2)(0.0, 1.0)` (正確，並傳回 `cos(1.0)`) ，而且不 `bind(cos, _2)(0.0)` 正確。

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

## <a name="bind1st"></a><a name="bind1st"></a> bind1st

Helper 範本函式，可建立將二元函式物件轉換成一元函式物件的介面卡。 它會將二元函數的第一個引數系結至指定的值。 在 c + + 11 中已被取代，在 c + + 17 中移除

```cpp
template <class Operation, class Type>
    binder1st <Operation> bind1st (const Operation& func, const Type& left);
```

### <a name="parameters"></a>參數

*func*\
要轉換為一元函式物件的二元函式物件。

*離開*\
二元函式物件的第一個引數所要繫結的值。

### <a name="return-value"></a>傳回值

一元函式物件，此物件是因為將二元函式物件的第一個引數系結至 *左方*的值所產生。

### <a name="remarks"></a>備註

函數系結器是一種函式配接器。 因為它們會傳回函式物件，所以可用於特定類型的函式組合，以建立更複雜且功能強大的運算式。

如果 *func* 是型別的物件， `Operation` 且 `c` 是常數，則與 `bind1st( func, c )` [binder1st](../standard-library/binder1st-class.md) 類別的函式相同 `binder1st<Operation>(func, c)` ，而且更方便使用。

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

## <a name="bind2nd"></a><a name="bind2nd"></a> bind2nd

Helper 範本函式，可建立將二元函式物件轉換成一元函式物件的介面卡。 它會將二元函數的第二個引數系結至指定的值。 在 c + + 11 中已被取代，在 c + + 17 中移除

```cpp
template <class Operation, class Type>
    binder2nd <Operation> bind2nd(const Operation& func, const Type& right);
```

### <a name="parameters"></a>參數

*func*\
要轉換為一元函式物件的二元函式物件。

*對*\
二元函式物件的第二個引數所要繫結的值。

### <a name="return-value"></a>傳回值

將二元函式物件的第二個引數系結至 *右邊*的一元函式物件結果。

### <a name="remarks"></a>備註

函數系結器是一種函式配接器。 因為它們會傳回函式物件，所以可用於特定類型的函式組合，以建立更複雜且功能強大的運算式。

如果 *func* 是型別的物件， `Operation` 且 `c` 是常數，則與 `bind2nd(func, c)` [binder2nd](../standard-library/binder2nd-class.md) 類別的函式相同 `binder2nd<Operation>(func, c)` ，而且更方便使用。

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

## <a name="bit_and"></a><a name="bit_and"></a> bit_and

預先定義的函式物件，會 `operator&` 在其引數上執行位 and 運算 (二元) 。

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

*Type*、 *T*、 *U*\
支援 `operator&` 的任何類型，其接受指定或推斷類型的運算元。

*離開*\
位元 AND 運算的左運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *T*的左值和右值參考引數。

*對*\
位元 AND 運算的右運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *U*的左值和右值參考引數。

### <a name="return-value"></a>傳回值

`Left & Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator&` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_and` 仿函數僅限於整數類型，或會實作二元 `operator&` 的使用者定義類型。

## <a name="bit_not"></a><a name="bit_not"></a> bit_not

一個預先定義的函式物件，會執行位補數 (不會) 運算 (一元 `operator~`) 引數。 在 c + + 14 中新增。

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
    auto operator()(Type&& Right) const -> decltype(~std::forward<Type>(Right));
};
```

### <a name="parameters"></a>參數

*類型*\
支援一元 `operator~` 的類型。

*對*\
位元補數運算的運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美轉送推斷類型 *類型*的左值或右值參考引數。

### <a name="return-value"></a>傳回值

`~ Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator~` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_not` 仿函數僅限於整數類型，或會實作二元 `operator~` 的使用者定義類型。

## <a name="bit_or"></a><a name="bit_or"></a> bit_or

在其引數上執行位 OR 運算 () 的預先定義函數物件 `operator|` 。

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
        -> decltype(std::forward<T>(Left) | std::forward<U>(Right));
};
```

### <a name="parameters"></a>參數

*Type*、 *T*、 *U*\
支援 `operator|` 的任何類型，其接受指定或推斷類型的運算元。

*離開*\
位元 OR 運算的左運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *T*的左值和右值參考引數。

*對*\
位元 OR 運算的右運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *U*的左值和右值參考引數。

### <a name="return-value"></a>傳回值

`Left | Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator|` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_or` 函式僅限於整數類型，或會實作 `operator|` 的使用者定義類型。

## <a name="bit_xor"></a><a name="bit_xor"></a> bit_xor

預先定義的函式物件，會 `operator^` 在其引數上執行位 XOR 運算 (二元) 。

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

*Type*、 *T*、 *U*\
支援 `operator^` 的任何類型，其接受指定或推斷類型的運算元。

*離開*\
位元 XOR 運算的左運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *T*的左值和右值參考引數。

*對*\
位元 XOR 運算的右運算元。 未特製化的範本會採用類型 *類型*的左值參考引數。 特製化的範本會完美地轉送推斷類型 *U*的左值和右值參考引數。

### <a name="return-value"></a>傳回值

`Left ^ Right` 的結果。 此特製化的範本會完美地轉送結果，其具有 `operator^` 所傳回的類型。

### <a name="remarks"></a>備註

對於基本資料類型，`bit_xor` 仿函數僅限於整數類型，或會實作二元 `operator^` 的使用者定義類型。

## <a name="cref"></a><a name="cref"></a> cref

從引數建構常數`reference_wrapper`。

```cpp
template <class Ty>
reference_wrapper<const Ty> cref(const Ty& arg);

template <class Ty>
reference_wrapper<const Ty> cref(const reference_wrapper<Ty>& arg);
```

### <a name="parameters"></a>參數

*泰*\
要包裝的引數類型。

*精 氨 酸*\
要包裝的引數。

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

## <a name="invoke"></a><a name="invoke"></a> 調用

使用指定的引數叫用任何可呼叫的物件。 在 c + + 17 中新增。

```cpp
template <class Callable, class... Args>
invoke_result_t<Callable, Args...>
    invoke(Callable&& fn, Args&&... args) noexcept(/* specification */);
```

### <a name="parameters"></a>參數

*調用*\
要呼叫的物件類型。

*參數*\
呼叫引數的類型。

*Fn*\
要呼叫的物件。

*參數*\
呼叫的引數。

*規範*\
**`noexcept`** 規格 `std::is_nothrow_invocable_v<Callable, Args>)` 。

### <a name="remarks"></a>備註

使用*參數自*變數叫用可呼叫物件*fn* 。 實際上， `INVOKE(std::forward<Callable>(fn), std::forward<Args>(args)...)` 虛擬函式是 `INVOKE(f, t1, t2, ..., tN)` 指下列其中一項：

- `(t1.*f)(t2, ..., tN)`：當 `f` 是 `T` 類別的成員函式指標，而且 `t1` 是 `T` 類型的物件、`T` 類型的物件參考或衍生自 `T` 之類型的物件參考時。 亦即，當 `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` 為 true 時。

- `(t1.get().*f)(t2, ..., tN)` 當 `f` 是類別的成員函式指標 `T` ，而且 `std::decay_t<decltype(t1)>` 是的特製化時 `std::reference_wrapper` 。

- `((*t1).*f)(t2, ..., tN)` 當 `f` 是類別的成員函式指標 `T` ，而 `t1` 不是先前的其中一個類型時。

- `t1.*f`：當 N == 1，`f` 是 `T` 類別的成員資料指標，而且 `t1` 是 `T` 類型的物件、`T` 類型的物件參考或衍生自 `T` 之類型的物件參考時。  亦即，當 `std::is_base_of<T, std::decay_t<decltype(t1)>>::value` 為 true 時。

- `t1.get().*f` 當 N = = 1，而且 `f` 是類別的成員資料指標 `T` ，而且是的特製 `std::decay_t<decltype(t1)>` 化時 `std::reference_wrapper` 。

- `(*t1).*f` 當 N = = 1，而且 `f` 是類別的成員資料指標 `T` ，而 `t1` 不是先前的其中一個類型時。

- `f(t1, t2, ..., tN)` (針對所有其他情況)。

如需可呼叫物件之結果類型的詳細資訊，請參閱 [invoke_result](invoke-result-class.md)。 如需可呼叫類型的述詞，請參閱 [is_invocable、is_invocable_r、is_nothrow_invocable is_nothrow_invocable_r 類別](is-invocable-classes.md)。

### <a name="example"></a>範例

```cpp
// functional_invoke.cpp
// compile using: cl /EHsc /std:c++17 functional_invoke.cpp
#include <functional>
#include <iostream>

struct Demo
{
    int n_;

    Demo(int const n) : n_{n} {}

    void operator()( int const i, int const j ) const
    {
        std::cout << "Demo operator( " << i << ", "
            << j << " ) is " << i * j << "\n";
    }

    void difference( int const i ) const
    {
        std::cout << "Demo.difference( " << i << " ) is "
            << n_ - i << "\n";
    }
};

void divisible_by_3(int const i)
{
    std::cout << i << ( i % 3 == 0 ? " is" : " isn't" )
        << " divisible by 3.\n";
}

int main()
{
    Demo d{ 42 };
    Demo * pd{ &d };
    auto pmf = &Demo::difference;
    auto pmd = &Demo::n_;

    // Invoke a function object, like calling d( 3, -7 )
    std::invoke( d, 3, -7 );

    // Invoke a member function, like calling
    // d.difference( 29 ) or (d.*pmf)( 29 )
    std::invoke( &Demo::difference, d, 29 );
    std::invoke( pmf, pd, 13 );

    // Invoke a data member, like access to d.n_ or d.*pmd
    std::cout << "d.n_: " << std::invoke( &Demo::n_, d ) << "\n";
    std::cout << "pd->n_: " << std::invoke( pmd, pd ) << "\n";

    // Invoke a stand-alone (free) function
    std::invoke( divisible_by_3, 42 );

    // Invoke a lambda
    auto divisible_by_7 = []( int const i ) {
        std::cout << i << ( i % 7 == 0 ? " is" : " isn't" )
            << " divisible by 7.\n";
        };
    std::invoke( divisible_by_7, 42 );
}
```

```Output
Demo operator( 3, -7 ) is -21
Demo.difference( 29 ) is 13
Demo.difference( 13 ) is 29
d.n_: 42
pd->n_: 42
42 is divisible by 3.
42 is divisible by 7.
```

## <a name="mem_fn"></a><a name="mem_fn"></a> mem_fn

產生簡單呼叫包裝函式。

```cpp
template <class RTy, class Ty>
unspecified mem_fn(RTy Ty::*pm);
```

### <a name="parameters"></a>參數

*RTy*\
包裝函式的傳回類型。

*泰*\
成員函式指標的類型。

### <a name="remarks"></a>備註

樣板函式會傳回簡單的呼叫包裝函式 `cw` ，其具有弱式結果類型，因此運算式與 `cw(t, a2, ..., aN)` 相同 `INVOKE(pm, t, a2, ..., aN)` 。 它不會擲回任何例外狀況。

傳回的呼叫包裝函式衍生自 `std::unary_function<cv Ty*, RTy>` (，並且將嵌套型別定義 `result_type` 為 *RTy* 的同義字，而將嵌套型別定義為 `argument_type`) 的同義字 `cv Ty*` 。只有在類型 *Ty* 是具有 `cv` 不採用任何引數之 cv 辨識符號的成員函式指標時

傳回的呼叫包裝函式衍生自 `std::binary_function<cv Ty*, T2, RTy>` (，並將嵌套型別定義 `result_type` 為 *RTy*的同義字、將嵌套型別 `first argument_type` 做為同義字 `cv Ty*` ，以及將巢狀型別定義為 `second argument_type`) 的同義字 `T2` 。只有當型別 *Ty* 是具有 cv 限定詞的成員函式指標時，才會使用型別為 `cv` 的一個引數 `T2` 。

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

## <a name="mem_fun"></a><a name="mem_fun"></a> mem_fun

協助程式樣板函式，可用來建構使用指標引數初始化時之成員函式的物件配接器。 在 c + + 11 中已淘汰 [mem_fn](#mem_fn) [和系結，並已](#bind)在 c + + 17 中移除。

```cpp
template <class Result, class Type>
mem_fun_t<Result, Type> mem_fun (Result(Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_t<Result, Type> mem_fun(Result (Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_t<Result, Type, Arg> mem_fun(Result (Type::* pMem)(Arg) const);
```

### <a name="parameters"></a>參數

*pMem*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

### <a name="return-value"></a>傳回值

或 **`const`** **non_const** 類型或的函式 `mem_fun_t` 物件 `mem_fun1_t` 。

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

## <a name="mem_fun_ref"></a><a name="mem_fun_ref"></a> mem_fun_ref

Helper 範本函式，用以在使用參考引數初始化時建構成員函式的物件配接器。 在 c + + 11 中已被取代，在 c + + 17 中移除

```cpp
template <class Result, class Type>
mem_fun_ref_t<Result, Type> mem_fun_ref(Result (Type::* pMem)());

template <class Result, class Type, class Arg>
mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (Type::* pMem)(Arg));

template <class Result, class Type>
const_mem_fun_ref_t<Result, Type> mem_fun_ref(Result Type::* pMem)() const);

template <class Result, class Type, class Arg>
const_mem_fun1_ref_t<Result, Type, Arg> mem_fun_ref(Result (T::* pMem)(Arg) const);
```

### <a name="parameters"></a>參數

*pMem*\
要轉換成函式物件之 `Type` 類別的成員函式指標。

### <a name="return-value"></a>傳回值

或 **`const`** 類型的或函式 `non_const` 物件 `mem_fun_ref_t` `mem_fun1_ref_t` 。

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

## <a name="not1"></a><a name="not1"></a> not1

傳回一元述詞的補數。 已針對 c + + 17 中的 [not_fn](#not_fn) 取代。

```cpp
template <class UnaryPredicate>
unary_negate<UnaryPredicate> not1(const UnaryPredicate& predicate);
```

### <a name="parameters"></a>參數

*謂詞*\
要變為負值的一元述詞。

### <a name="return-value"></a>傳回值

一元述詞，其為所修改之一元述詞的負值。

### <a name="remarks"></a>備註

如果是從一元述詞所建立，則會傳回 `unary_negate` `predicate(x)` `!predicate(x)` 。

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

## <a name="not2"></a><a name="not2"></a> not2

傳回二元述詞的補數。 已針對 c + + 17 中的 [not_fn](#not_fn) 取代。

```cpp
template <class BinaryPredicate>
binary_negate<BinaryPredicate> not2(const BinaryPredicate& func);
```

### <a name="parameters"></a>參數

*func*\
要變為負值的二元述詞。

### <a name="return-value"></a>傳回值

二元述詞，其為所修改之二元述詞的負值。

### <a name="remarks"></a>備註

如果 `binary_negate` 是從二元述詞所構成 `binary_predicate(x, y)` ，則會傳回 `!binary_predicate(x, y)` 。

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

## <a name="not_fn"></a><a name="not_fn"></a> not_fn

函式 `not_fn` 範本會接受可呼叫的物件，並傳回可呼叫的物件。 稍後使用一些引數叫用傳回的可呼叫物件時，會將它們傳遞給原始的可呼叫物件，並以邏輯方式否定結果。 它會保留已包裝之可呼叫物件的 const 限定和值類別行為。 `not_fn` 是 c + + 17 的新功能，取代了已淘汰的 `std::not1` 、、 `std::not2` `std::unary_negate` 和 `std::binary_negate` 。

```cpp
template <class Callable>
/* unspecified */ not_fn(Callable&& func);
```

### <a name="parameters"></a>參數

*func*\
用來建立轉送呼叫包裝函式的可呼叫物件。

### <a name="remarks"></a>備註

範本函 `return call_wrapper(std::forward<Callable>(func))` 式會根據這個僅限展示類別，傳回類似的呼叫包裝函式：

```cpp
class call_wrapper
{
   using FD = decay_t<Callable>;
   explicit call_wrapper(Callable&& func);

public:
   call_wrapper(call_wrapper&&) = default;
   call_wrapper(call_wrapper const&) = default;

   template<class... Args>
     auto operator()(Args&&...) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());

   template<class... Args>
     auto operator()(Args&&...) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());

private:
  FD fd;
};
```

可呼叫物件 *func* 上的明確的函式需要型別 `std::decay_t<Callable>` 來滿足的需求 `MoveConstructible` ，而且 `is_constructible_v<FD, Callable>` 必須是 true。 它會從初始化包裝的可呼叫物件，並擲回由的結構擲回的 `fd` `std::forward<Callable>(func)` 任何例外狀況 `fd` 。

包裝函式會公開由左值或右值參考分類和 const 限定性所區分的呼叫運算子，如下所示：

```cpp
template<class... Args> auto operator()(Args&&... args) & -> decltype(!declval<invoke_result_t<FD&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const& -> decltype(!declval<invoke_result_t<FD const&(Args...)>>());
template<class... Args> auto operator()(Args&&... args) && -> decltype(!declval<invoke_result_t<FD(Args...)>>());
template<class... Args> auto operator()(Args&&... args) const&& -> decltype(!declval<invoke_result_t<FD const(Args...)>>());
```

前兩個與相同 `return !std::invoke(fd, std::forward<Args>(args)...)` 。 第二個則是相同的 `return !std::invoke(std::move(fd), std::forward<Args>(args)...)` 。

### <a name="example"></a>範例

```cpp
// functional_not_fn_.cpp
// compile with: /EHsc /std:c++17
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    std::vector<int> v1 = { 99, 6264, 41, 18467, 6334, 26500, 19169 };
    auto divisible_by_3 = [](int i){ return i % 3 == 0; };

    std::cout << "Vector v1 = ( " ;
    for (const auto& item : v1)
    {
        std::cout << item << " ";
    }
    std::cout << ")" << std::endl;

    // Count the number of vector elements divisible by 3.
    int divisible =
        std::count_if(v1.begin(), v1.end(), divisible_by_3);
    std::cout << "Elements divisible by three: "
        << divisible << std::endl;

    // Count the number of vector elements not divisible by 3.
    int not_divisible =
        std::count_if(v1.begin(), v1.end(), std::not_fn(divisible_by_3));
    std::cout << "Elements not divisible by three: "
        << not_divisible << std::endl;
}
```

```Output
Vector v1 = ( 99 6264 41 18467 6334 26500 19169 )
Elements divisible by three: 2
Elements not divisible by three: 5
```

## <a name="ptr_fun"></a><a name="ptr_fun"></a> ptr_fun

Helper 範本函式，可用來將一元和二元函式指標分別轉換成一元和二元可調適性函式。 在 c + + 11 中已被取代，在 c + + 17 中移除

```cpp
template <class Arg, class Result>
pointer_to_unary_function<Arg, Result, Result (*)(Arg)> ptr_fun(Result (*pfunc)(Arg));

template <class Arg1, class Arg2, class Result>
pointer_to_binary_function<Arg1, Arg2, Result, Result (*)(Arg1, Arg2)> ptr_fun(Result (*pfunc)(Arg1, Arg2));
```

### <a name="parameters"></a>參數

*>pfunc*\
要轉換成可調適性函式的一元或二元函式指標。

### <a name="return-value"></a>傳回值

第一個範本函式會傳回一元函式[pointer_to_unary_function](../standard-library/pointer-to-unary-function-class.md)  < `Arg` 、**結果**> (\* `pfunc`) 。

第二個樣板函式會傳回二元函數 [pointer_to_binary_function](../standard-library/pointer-to-binary-function-class.md) \<**Arg1**, **Arg2**, **Result**> (\* `pfunc`) 。

### <a name="remarks"></a>備註

函式指標是函式物件。 它可以傳遞給任何需要函式作為參數的演算法，但它並不是可調整的。 例如，若要將值系結至該介面卡或將其設為否定，則需要其巢狀型別的相關資訊。 由 `ptr_fun` helper 函式進行的一元和二元函式指標轉換，可讓函式配接器使用一元和二元函式指標。

### <a name="example"></a>範例

[!code-cpp[functional_ptr_fun#1](../standard-library/codesnippet/CPP/functional-functions_1.cpp)]

## <a name="ref"></a><a name="ref"></a> 裁判

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

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個 `function` 物件。

```cpp
template <class FT>
    void swap(function<FT>& f1, function<FT>& f2);
```

### <a name="parameters"></a>參數

*英尺*\
函式物件所控制的類型。

*按*\
第一個函式物件。

*進入*\
第二個函式物件。

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

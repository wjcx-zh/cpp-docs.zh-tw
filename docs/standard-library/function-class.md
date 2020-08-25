---
title: function 類別
ms.date: 11/04/2016
f1_keywords:
- functional/std::function
- functional/std::function::result_type
- functional/std::function::assign
- functional/std::function::swap
- functional/std::function::target
- functional/std::function::target_type
- functional/std::function::operator unspecified
- functional/std::function::operator()
helpviewer_keywords:
- std::function [C++]
- std::function [C++], result_type
- std::function [C++], assign
- std::function [C++], swap
- std::function [C++], target
- std::function [C++], target_type
ms.assetid: 7b5ca76b-9ca3-4d89-8fcf-cad70a4aeae6
ms.openlocfilehash: 052cbba69aa99d33de963a3e360e6951a6006bec
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831459"
---
# <a name="function-class"></a>function 類別

可呼叫物件的包裝函式。

## <a name="syntax"></a>語法

```cpp
template <class Fty>
class function  // Fty of type Ret(T1, T2, ..., TN)
    : public unary_function<T1, Ret>       // when Fty is Ret(T1)
    : public binary_function<T1, T2, Ret>  // when Fty is Ret(T1, T2)
{
public:
    typedef Ret result_type;

    function();
    function(nullptr_t);
    function(const function& right);
    template <class Fty2>
        function(Fty2 fn);
    template <class Fty2, class Alloc>
        function(reference_wrapper<Fty2>, const Alloc& Ax);

    template <class Fty2, class Alloc>
        void assign(Fty2, const Alloc& Ax);
    template <class Fty2, class Alloc>
        void assign(reference_wrapper<Fty2>, const Alloc& Ax);
    function& operator=(nullptr_t);
    function& operator=(const function&);
    template <class Fty2>
        function& operator=(Fty2);
    template <class Fty2>
        function& operator=(reference_wrapper<Fty2>);

    void swap(function&);
    explicit operator bool() const;

    result_type operator()(T1, T2, ....., TN) const;
    const std::type_info& target_type() const;
    template <class Fty2>
        Fty2 *target();

    template <class Fty2>
        const Fty2 *target() const;

    template <class Fty2>
        void operator==(const Fty2&) const = delete;
    template <class Fty2>
        void operator!=(const Fty2&) const = delete;
};
```

### <a name="parameters"></a>參數

*廠*\
要包裝的函式類型。

*斧頭*\
配置器函數。

## <a name="remarks"></a>備註

類別樣板是呼叫簽章為的呼叫包裝函式 `Ret(T1, T2, ..., TN)` 。 在統一包裝函式中，您可以使用此項目來括住各種可呼叫的物件。

有些成員函式會採用運算元來命名所需的目標物件。 您可以透過數種方法指定這類運算元：

`fn` -- 可呼叫物件 `fn`；呼叫之後，`function` 物件會保留 `fn` 的複本。

`fnref` -- 由 `fnref.get()` 命名的可呼叫物件；呼叫之後，`function` 物件會保留 `fnref.get()` 的參考。

`right` -- 由 `function` 物件 `right` 保存的可呼叫的物件 (如果有的話)。

`npc` -- null 指標；在呼叫之後，`function` 物件是空的。

在所有情況下，`INVOKE(f, t1, t2, ..., tN)` 都必須語式正確 (其中 `f` 是可呼叫物件，而 `t1, t2, ..., tN` 分別是 `T1, T2, ..., TN` 類型的左值)；如果 `Ret` 不是 void，則會轉換為 `Ret`。

空的 `function` 物件不會保留可呼叫物件或可呼叫物件的參考。

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[函數](#function)|可建構空的包裝函式，或儲存含固定簽章的任意類型可呼叫物件。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|-|-|
|[result_type](#result_type)|為預存的可呼叫物件的傳回類型。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[assign](#assign)|會將可呼叫物件指派給此函式物件。|
|[交換](#swap)|交換兩個可呼叫物件。|
|[目標](#target)|測試預存的可呼叫物件是否如指定般為可呼叫。|
|[target_type](#target_type)|取得可呼叫物件的類型資訊。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[未指定運算子](#op_unspecified)|測試預存的可呼叫物件是否存在。|
|[運算子 ( # B1 ](#op_call)|呼叫可呼叫物件。|
|[運算子 =](#op_eq)|取代預存的可呼叫物件。|

## <a name="assign"></a><a name="assign"></a> 分配

會將可呼叫物件指派給此函式物件。

```cpp
template <class Fx, class Alloc>
    void assign(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    void assign(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>參數

*_Func*\
可呼叫的物件。

*_Fnref*\
參考包裝函式，其中包含可呼叫物件。

*斧頭*\
配置器物件。

### <a name="remarks"></a>備註

成員函式每個都會 `callable object` 以傳遞的可呼叫物件來取代所持有的 **`*this`** `operand` 。 使用配置器物件 *Ax*配置儲存體。

## <a name="function"></a><a name="function"></a> 函式

可建構空的包裝函式，或儲存含固定簽章的任意類型可呼叫物件。

```cpp
function();
function(nullptr_t npc);
function(const function& right);
template <class Fx>
    function(Fx _Func);
template <class Fx>
    function(reference_wrapper<Fx> _Fnref);
template <class Fx, class Alloc>
    function(
        Fx _Func,
        const Alloc& Ax);

template <class Fx, class Alloc>
    function(
        reference_wrapper<Fx> _Fnref,
        const Alloc& Ax);
```

### <a name="parameters"></a>參數

*對*\
要複製的函式物件。

*外匯*\
可呼叫物件的類型。

*_Func*\
要包裝的可呼叫物件。

*配置*\
配置器類型。

*斧頭*\
配置器。

*_Fnref*\
要包裝的可呼叫物件參考。

### <a name="remarks"></a>備註

前兩個建構函式會建構空的 `function` 物件。 接下來的三個建構函式會建構 `function` 物件，其中保留以運算元傳遞的可呼叫物件。 最後兩個建構函式會使用配置器物件 Ax 來配置儲存體。

### <a name="example"></a>範例

```cpp
// std__functional__function_function.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>
#include <vector>

int square(int val)
{
    return val * val;
}

class multiply_by
{
public:
    explicit multiply_by(const int n) : m_n(n) { }

    int operator()(const int x) const
    {
        return m_n * x;
    }

private:
    int m_n;
};

int main()
{

    typedef std::vector< std::function<int (int)> > vf_t;

    vf_t v;
    v.push_back(square);
    v.push_back(std::negate<int>());
    v.push_back(multiply_by(3));

    for (vf_t::const_iterator i = v.begin(); i != v.end(); ++i)
    {
        std::cout << (*i)(10) << std::endl;
    }

    std::function<int (int)> f = v[0];
    std::function<int (int)> g;

    if (f) {
        std::cout << "f is non-empty (correct)." << std::endl;
    } else {
        std::cout << "f is empty (can't happen)." << std::endl;
    }

    if (g) {
        std::cout << "g is non-empty (can't happen)." << std::endl;
    } else {
        std::cout << "g is empty (correct)." << std::endl;
    }

    return 0;
}
```

```Output
100
-10
30
f is non-empty (correct).
g is empty (correct).
```

## <a name="operator-unspecified"></a><a name="op_unspecified"></a> 未指定運算子

測試預存的可呼叫物件是否存在。

```cpp
operator unspecified();
```

### <a name="remarks"></a>備註

只有當物件不是空的時，運算子才會傳回可轉換成 **`bool`** true 值的值。 您可以使用它來測試物件是否是空的。

### <a name="example"></a>範例

```cpp
// std__functional__function_operator_bool.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == " << (bool)fn0 << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == " << (bool)fn1 << std::endl;

    return (0);
    }
```

```Output
not empty == false
not empty == true
```

## <a name="operator"></a><a name="op_call"></a> 運算子 ( # A1

呼叫可呼叫物件。

```cpp
result_type operator()(
    T1 t1,
    T2 t2, ...,
    TN tN);
```

### <a name="parameters"></a>參數

*Tn*\
第 N 個呼叫引數類型。

*Tn*\
第 N 個呼叫引數。

### <a name="remarks"></a>備註

成員函式 `INVOKE(fn, t1, t2, ..., tN, Ret)` 會傳回，其中 `fn` 是儲存在中的目標物件 **`*this`** 。 您可以使用此項目來呼叫已包裝的可呼叫物件。

### <a name="example"></a>範例

```cpp
// std__functional__function_operator_call.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

取代預存的可呼叫物件。

```cpp
function& operator=(null_ptr_type npc);
function& operator=(const function& right);
template <class Fty>
    function& operator=(Fty fn);
template <class Fty>
    function& operator=(reference_wrapper<Fty> fnref);
```

### <a name="parameters"></a>參數

*全國 人大*\
null 指標常數。

*對*\
要複製的函式物件。

*Fn*\
要包裝的可呼叫物件。

*fnref*\
要包裝的可呼叫物件參考。

### <a name="remarks"></a>備註

每個運算子都會將所持有的可呼叫物件 **`*this`** ，取代為作為運算元傳遞的可呼叫物件。

### <a name="example"></a>範例

```cpp
// std__functional__function_operator_as.cpp
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
    fn1 = 0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    fn1 = neg;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = fn0;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    fn1 = std::cref(fn1);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "val == " << fn1(3) << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
empty == true
empty == false
val == -3
empty == false
val == -3
empty == false
val == -3
```

## <a name="result_type"></a><a name="result_type"></a> result_type

為預存的可呼叫物件的傳回類型。

```cpp
typedef Ret result_type;
```

### <a name="remarks"></a>備註

typedef 與範本呼叫簽章中的 `Ret` 類型同義。 您可以使用它來判斷所包裝之可呼叫物件的傳回類型。

### <a name="example"></a>範例

```cpp
// std__functional__function_result_type.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;

    std::function<int (int)>::result_type val = fn1(3);
    std::cout << "val == " << val << std::endl;

    return (0);
    }
```

```Output
empty == false
val == -3
```

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個可呼叫物件。

```cpp
void swap(function& right);
```

### <a name="parameters"></a>參數

*對*\
要交換的函式物件。

### <a name="remarks"></a>備註

成員函式會交換 **`*this`** 和 *右邊*的目標物件。 它會在固定時間執行但不會擲回任何例外狀況。

### <a name="example"></a>範例

```cpp
// std__functional__function_swap.cpp
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

    fn0.swap(fn1);
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

## <a name="target"></a><a name="target"></a> 目標

測試預存的可呼叫物件是否如指定般為可呼叫。

```cpp
template <class Fty2>
    Fty2 *target();
template <class Fty2>
    const Fty2 *target() const;
```

### <a name="parameters"></a>參數

*Fty2*\
要測試的目標可呼叫物件類型。

### <a name="remarks"></a>備註

型別 *Fty2* 必須可供引數類型 `T1, T2, ..., TN` 和傳回型別呼叫 `Ret` 。 如果 `target_type() == typeid(Fty2)`，成員範本函式會傳回目標物件的位址；否則會傳回 0。

型別 *Fty2* 可供引數型別 `T1, T2, ..., TN` 和傳回型別呼叫，如果的類型 `Ret` `fn, t1, t2, ..., tN` `Fty2, T1, T2, ..., TN` 分別是格式正確， `INVOKE(fn, t1, t2, ..., tN)` 而且如果不 `Ret` 是，則 **`void`** 可以轉換成 `Ret` 。

### <a name="example"></a>範例

```cpp
// std__functional__function_target.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    typedef int (*Myfun)(int);
    std::function<int (int)> fn0(neg);
    std::cout << std::boolalpha << "empty == " << !fn0 << std::endl;
    std::cout << "no target == " << (fn0.target<Myfun>() == 0) << std::endl;

    Myfun *fptr = fn0.target<Myfun>();
    std::cout << "val == " << (*fptr)(3) << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "no target == " << (fn1.target<Myfun>() == 0) << std::endl;

    return (0);
    }
```

```Output
empty == false
no target == false
val == -3
empty == true
no target == true
```

## <a name="target_type"></a><a name="target_type"></a> target_type

取得可呼叫物件的類型資訊。

```cpp
const std::type_info& target_type() const;
```

### <a name="remarks"></a>備註

如果是空的，則成員函式會傳回，否則會傳回 `typeid(void)` **`*this`** `typeid(T)` ，其中 `T` 是目標物件的類型。

### <a name="example"></a>範例

```cpp
// std__functional__function_target_type.cpp
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
    std::cout << "type == " << fn0.target_type().name() << std::endl;

    std::function<int (int)> fn1;
    std::cout << std::boolalpha << "empty == " << !fn1 << std::endl;
    std::cout << "type == " << fn1.target_type().name() << std::endl;

    return (0);
    }
```

```Output
empty == false
type == int (__cdecl*)(int)
empty == true
type == void
```

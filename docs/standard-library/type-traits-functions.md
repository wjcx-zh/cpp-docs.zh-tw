---
title: '&lt;type_traits&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
- type_traits/std::is_copy_assignable
- type_traits/std::is_copy_constructible
- type_traits/std::is_default_constructible
- type_traits/std::is_move_assignable
- type_traits/std::is_move_constructible
- type_traits/std::is_nothrow_move_assignable
- type_traits/std::is_trivially_copy_assignable
- type_traits/std::is_trivially_move_assignable
- type_traits/std::is_trivially_move_constructible
ms.assetid: dce4492f-f3e4-4d5e-bdb4-5875321254ec
helpviewer_keywords:
- std::is_assignable
- std::is_copy_assignable
- std::is_copy_constructible
- std::is_default_constructible
- std::is_move_assignable
- std::is_move_constructible
- std::is_nothrow_move_assignable
- std::is_trivially_copy_assignable
- std::is_trivially_move_assignable
- std::is_trivially_move_constructible
ms.openlocfilehash: 027ed3052f5341860112f564974b7a96aea7ff51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399404"
---
# <a name="lttypetraitsgt-functions"></a>&lt;type_traits&gt; 函式

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|[is_trivially_move_assignable](#is_trivially_move_assignable)|
|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable

測試的值是否*從*型別可以指派給*到*型別。

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>參數

*若要*<br/>
接收指派的物件類型。

*From*<br/>
提供值的物件類型。

### <a name="remarks"></a>備註

未評估的運算式 `declval<To>() = declval<From>()` 必須格式正確。 兩者*從*並*要*必須是完整的類型**void**，或界限未知的陣列。

## <a name="is_copy_assignable"></a>  is_copy_assignable

測試類型是否可以在指派上複製。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有複製指派運算子，否則為 false 的類別。 相當於 is_assignable\<Ty&, const Ty&>。

## <a name="is_copy_constructible"></a>  is_copy_constructible

測試類型是否有複製建構函式。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是複製建構函式，否則為 false 的類別。

### <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

struct Copyable
{
    int val;
};

struct NotCopyable
{
   NotCopyable(const NotCopyable&) = delete;
   int val;

};

int main()
{
    std::cout << "is_copy_constructible<Copyable> == " << std::boolalpha
        << std::is_copy_constructible<Copyable>::value << std::endl;
    std::cout << "is_copy_constructible<NotCopyable> == " << std::boolalpha
        << std::is_copy_constructible<NotCopyable>::value << std::endl;

    return (0);
}
```

```Output
is_copy_constructible<Copyable> == true
is_copy_constructible<NotCopyable > == false
```

## <a name="is_default_constructible"></a>  is_default_constructible

測試類型是否有預設建構函式。

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是類別類型具有預設建構函式，否則為 false。 這相當於述詞 `is_constructible<T>`。 型別*T*必須是完整的型別**void**，或是界限未知的陣列。

### <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}
```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="is_move_assignable"></a>  is_move_assignable

測試類型是否可以移動指派。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果對類型的 rvalue 參考可以指派給對類型的參考，該類型即為可透過移動方式指派的類型。 類型述詞相當於 `is_assignable<T&, T&&>`。 可移動指派的類型包含可參考的純量類型和類別類型，而且有由編譯器產生或使用者定義的移動指派運算子。

## <a name="is_move_constructible"></a>  is_move_constructible

測試類型是否有移動建構函式。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T*<br/>
要評估的類型

### <a name="remarks"></a>備註

類型述詞評估為 true 的型別*T*可以藉由使用移動作業建構。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

測試類型是否有 **nothrow** 移動指派運算子。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*具有 nothrow 移動指派運算子，否則為 false。

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

測試類型是否有 trivial 複製指派運算子。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>參數

*T*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是具有 trivial 複製指派運算子，否則為 false 的類別。

類別的指派建構函式*T*微不足道，如果它以隱含方式提供，類別*T*沒有虛擬函式類別*T*沒有虛擬基底類別類別類型的所有非靜態資料成員都有 trivial 指派運算子和陣列的類別類型的所有非靜態資料成員的類別具有 trivial 指派運算子。

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

測試類型是否有 trivial 移動指派運算子。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有 trivial 移動指派運算子，否則為 false 的類別。

類別的移動指派運算子*Ty*輕而易舉的事如果：

它會隱含地提供

此類別*Ty*沒有虛擬函式

此類別*Ty*沒有虛擬基底

類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子

類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

測試類型是否有 trivial 移動建構函式。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

### <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是具有 trivial 移動建構函式，否則為 false 的類別。

類別的移動建構函式*Ty*輕而易舉的事如果：

它是隱含宣告

其參數類型相等於隱含宣告的參數類型

此類別*Ty*沒有虛擬函式

此類別*Ty*沒有虛擬基底

類別沒有任何變動性的非靜態資料成員

所有直接基都底類別的*Ty*具有 trivial 移動建構函式

類別類型的所有非靜態資料成員的類別都具有 trivial 移動建構函式

類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 移動建構函式

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>

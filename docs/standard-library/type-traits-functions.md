---
title: '&lt;type_traits&gt; 函式'
ms.date: 11/04/2016
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
ms.openlocfilehash: 40ebd24a286039391dedacf289d305ee5ec9ca95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447473"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; 函式

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a>  is_assignable

測試是否可以將*From*類型的值指派*給類型。*

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>參數

*若要*\
接收指派的物件類型。

*從*\
提供值的物件類型。

### <a name="remarks"></a>備註

未評估的運算式 `declval<To>() = declval<From>()` 必須格式正確。 *From*和*To*都必須是完整的類型、 **void**或未知系結的陣列。

## <a name="is_copy_assignable"></a>  is_copy_assignable

測試類型是否可以在指派上複製。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*是具有複製指派運算子的類別，則類型述詞的實例會保留 true，否則會保留 false。 相當於 is_assignable\<Ty&, const Ty&>。

## <a name="is_copy_constructible"></a>  is_copy_constructible

測試類型是否有複製建構函式。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*是具有複製參數的類別，則類型述詞的實例為 true，否則為 false。

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

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*T*是具有預設的構造函式的類別類型，則類型述詞的實例為 true，否則為 false。 這相當於述詞 `is_constructible<T>`。 類型*T*必須是完整的類型、 **void**，或未知系結的陣列。

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

測試是否可對類型進行移動指派。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>參數

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果對類型的 rvalue 參考可以指派給對類型的參考，該類型即為可透過移動方式指派的類型。 類型述詞相當於 `is_assignable<T&, T&&>`。 可移動指派的類型包含可參考的純量類型和類別類型，而且有由編譯器產生或使用者定義的移動指派運算子。

## <a name="is_move_constructible"></a>  is_move_constructible

測試類型是否具有移動建構函式。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T*\
要評估的類型

### <a name="remarks"></a>備註

如果可以使用 move 作業來建立類型*T* ，則會評估為 true 的類型述詞。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="is_nothrow_move_assignable"></a>  is_nothrow_move_assignable

測試類型是否具有 **nothrow** 移動指派運算子。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

### <a name="remarks"></a>備註

如果型別*Ty*有 nothrow 的移動指派運算子，則型別述詞的實例為 true，否則保留 false。

## <a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a>  is_trivially_copy_assignable

測試類型是否有 trivial 複製指派運算子。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>參數

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*T*是具有簡單複製指派運算子的類別，則類型述詞的實例為 true，否則為 false。

類別*t*的指派函式如果隱含提供 *，類別 t 不會有任何*虛擬函式、類別*t*沒有虛擬基底、類別類型之所有非靜態資料成員的類別都有簡單的指派運算子，而類別之類型陣列的所有非靜態資料成員的類別都有簡單的指派運算子。

## <a name="is_trivially_move_assignable"></a>  is_trivially_move_assignable

測試類型是否有 trivial 移動指派運算子。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*是具有簡單的移動指派運算子的類別，則類型述詞的實例為 true，否則為 false。

*Ty*類別的移動指派運算子在下列情況中是很簡單的：

它會隱含地提供

類別*Ty*沒有虛擬函式

類別*Ty*沒有虛擬基底

類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子

類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子

## <a name="is_trivially_move_constructible"></a>  is_trivially_move_constructible

測試類型是否有 trivial 移動建構函式。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>參數

*Ty*\
要查詢的類型。

### <a name="remarks"></a>備註

如果型別*Ty*是具有簡單的移動函式的類別，則類型述詞的實例為 true，否則為 false。

如果有下列情況，類別*Ty*的移動函式就很簡單：

它是隱含宣告

其參數類型相等於隱含宣告的參數類型

類別*Ty*沒有虛擬函式

類別*Ty*沒有虛擬基底

類別沒有任何變動性的非靜態資料成員

類別*Ty*的所有直接基底都有簡單的移動函式

類別類型的所有非靜態資料成員的類別都具有 trivial 移動建構函式

類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 移動建構函式

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)

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
ms.openlocfilehash: bc25c82629139c5bc2f6fa53d3555068374dca35
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367991"
---
# <a name="lttype_traitsgt-functions"></a>&lt;type_traits&gt; 函式

||||
|-|-|-|
|[is_assignable](#is_assignable)|[is_copy_assignable](#is_copy_assignable)|[is_copy_constructible](#is_copy_constructible)|
|[is_default_constructible](#is_default_constructible)|[is_move_assignable](#is_move_assignable)|[is_move_constructible](#is_move_constructible)|
|[is_nothrow_move_assignable](#is_nothrow_move_assignable)|[is_nothrow_swappable](#is_nothrow_swappable)|[is_nothrow_swappable_with](#is_nothrow_swappable_with)|
|[is_swappable](#is_swappable)|[is_swappable_with](#is_swappable_with)|[is_trivially_copy_assignable](#is_trivially_copy_assignable)|
|[is_trivially_move_assignable](#is_trivially_move_assignable)|[is_trivially_move_constructible](#is_trivially_move_constructible)|

## <a name="is_assignable"></a><a name="is_assignable"></a>is_assignable

測試 *"From"* 類型的值是否可以分配給 *"到"* 類型。

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>參數

*自*\
接收指派的物件類型。

*從*\
提供值的物件類型。

### <a name="remarks"></a>備註

未評估的運算式 `declval<To>() = declval<From>()` 必須格式正確。 *From*和*To*都必須是完整類型 **、void**或未知綁定的陣列。

## <a name="is_copy_assignable"></a><a name="is_copy_assignable"></a>is_copy_assignable

測試類型是否可以在指派上複製。

```cpp
template <class Ty>
struct is_copy_assignable;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*的類型是具有副本賦值運算符的類,則類型謂詞的實例為 true,否則它持有 false。 相當於 is_assignable\<Ty&, const Ty&>。

## <a name="is_copy_constructible"></a><a name="is_copy_constructible"></a>is_copy_constructible

測試類型是否有複製建構函式。

```cpp
template <class Ty>
struct is_copy_constructible;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*的類型是具有複製構造函數的類,則類型謂詞的實例為 true,否則它持有 false。

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

## <a name="is_default_constructible"></a><a name="is_default_constructible"></a>is_default_constructible

測試類型是否有預設建構函式。

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>參數

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*T*的類型是具有預設建構函數的類類型,則類型謂詞的實例為 true,否則它持有 false。 這相當於述詞 `is_constructible<T>`。 *類型 T*必須是完整類型、**空隙**或未知綁定的陣列。

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

## <a name="is_move_assignable"></a><a name="is_move_assignable"></a>is_move_assignable

測試類型是否可以移動指派。

```cpp
template <class T>
struct is_move_assignable;
```

### <a name="parameters"></a>參數

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果對類型的 rvalue 參考可以指派給對類型的參考，該類型即為可透過移動方式指派的類型。 類型述詞相當於 `is_assignable<T&, T&&>`。 可移動指派的類型包含可參考的純量類型和類別類型，而且有由編譯器產生或使用者定義的移動指派運算子。

## <a name="is_move_constructible"></a><a name="is_move_constructible"></a>is_move_constructible

測試類型是否有移動建構函式。

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>參數

*T*\
要評估的類型

### <a name="remarks"></a>備註

類型謂詞,如果可以使用移動操作構造類型*T,* 則計算為 true。 這個述詞相當於 `is_constructible<T, T&&>`。

## <a name="is_nothrow_move_assignable"></a><a name="is_nothrow_move_assignable"></a>is_nothrow_move_assignable

測試類型是否有 **nothrow** 移動指派運算子。

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型。

### <a name="remarks"></a>備註

如果*類型 Ty*具有無引發移動賦值運算符,則類型謂詞的實例為 true,否則該實例為 false。

## <a name="is_nothrow_swappable"></a><a name="is_nothrow_swappable"></a>is_nothrow_swappable

```cpp
template <class T> struct is_nothrow_swappable;
```

## <a name="is_nothrow_swappable_with"></a><a name="is_nothrow_swappable_with"></a>is_nothrow_swappable_with

```cpp
template <class T, class U> struct is_nothrow_swappable_with;
```

## <a name="is_swappable"></a><a name="is_swappable"></a>is_swappable

```cpp
template <class T> struct is_swappable;
```

## <a name="is_swappable_with"></a><a name="is_swappable_with"></a>is_swappable_with

```cpp
template <class T, class U> struct is_swappable_with;
```

## <a name="is_trivially_copy_assignable"></a><a name="is_trivially_copy_assignable"></a>is_trivially_copy_assignable

測試類型是否有 trivial 複製指派運算子。

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>參數

*T*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*T*的類型是具有普通副本賦值運算符的類,則類型謂詞的實例為 true,否則它持有 false。

如果隱式提供類*T*的賦值構造函數,則*類 T*沒有虛擬函數,類*T*沒有虛擬基,類類型的所有非靜態數據成員的類具有微不足道的賦值運算符,並且類類型數位的所有非靜態數據成員的類具有微不足道的賦值運算符,則該構造函數是微不足道的。

## <a name="is_trivially_move_assignable"></a><a name="is_trivially_move_assignable"></a>is_trivially_move_assignable

測試類型是否有 trivial 移動指派運算子。

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*的類型是具有瑣碎的移動賦值運算符的類,則類型謂詞的實例為 true,否則它持有 false。

如果 *:*

它會隱含地提供

類別*的 D- D- D- D*

*Ty*類別沒有虛擬基礎

類別類型的所有非靜態資料成員的類別具有 trivial 移動指派運算子

類別的類型陣列的所有非靜態資料成員的類別具有 trivial 移動指派運算子

## <a name="is_trivially_move_constructible"></a><a name="is_trivially_move_constructible"></a>is_trivially_move_constructible

測試類型是否有 trivial 移動建構函式。

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>參數

*泰*\
要查詢的類型。

### <a name="remarks"></a>備註

如果類型*Ty*的類型是具有瑣碎移動構造函數的類,則類型謂詞的實例為 true,否則它持有 false。

如果 *:*

它是隱含宣告

其參數類型相等於隱含宣告的參數類型

類別*的 D- D- D- D*

*Ty*類別沒有虛擬基礎

類別沒有任何變動性的非靜態資料成員

*Ty*類別的所有直接基礎都有瑣碎的移動建構函數

類別類型的所有非靜態資料成員的類別都具有 trivial 移動建構函式

類別的類型陣列的所有非靜態資料成員的類別，都具有 trivial 移動建構函式

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)

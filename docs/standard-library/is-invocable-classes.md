---
title: is_invocable、is_invocable_r、is_nothrow_invocable、is_nothrow_invocable_r 類別
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 20fec55fc3ad1924ee85db3b2f78812e4847f447
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456224"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable、is_invocable_r、is_nothrow_invocable、is_nothrow_invocable_r 類別

這些範本會判斷是否可以使用指定的引數類型叫用類型。 `is_invocable_r``is_nothrow_invocable_r`也會判斷調用的結果是否可轉換成特定類型。 `is_nothrow_invocable``is_nothrow_invocable_r`也會判斷調用是否已知不會擲回例外狀況。 已在 c + + 17 中新增。

## <a name="syntax"></a>語法

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>參數

*多次*\
要查詢的可呼叫類型。

*引數*\
要查詢的引數類型。

*轉換*\
可呼叫的結果類型必須可轉換為。

## <a name="remarks"></a>備註

如果`is_invocable`可以使用未評估內容中的 arguments 引數來叫用可呼叫的型別, 則型別述詞會保留 true。

如果`is_invocable_r`可以使用未評估內容中的 arguments 引數來叫用可呼叫的型別, 以產生可轉換成*可轉換*的結果型別, 則型別述詞會保留 true。

如果`is_nothrow_invocable`可以使用未評估內容中的 arguments 引數來叫用可呼叫的型別, 而且這類呼叫不會擲回例外狀況, 則型別述詞會保留 true。

如果`is_nothrow_invocable_r`可以使用未評估內容中的 arguments 引數來叫用可呼叫的型別, 使結果型別可轉換為*可轉換*, 而且這類呼叫不會擲回, 則型別述詞會保留 true。 例外狀況。

每一個*可轉換*、可呼叫的類型, 以及參數封裝引數中的類型, 都必須是完整的類型、未知系結的陣列, 或可能是 cv 限定的**void**。 否則, 不會定義述詞的行為。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value ); 
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>需求

**標頭：** \<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)

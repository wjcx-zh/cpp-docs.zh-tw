---
title: is_invocable、 is_invocable_r、 is_nothrow_invocable、 is_nothrow_invocable_r 類別
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
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336227"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable、 is_invocable_r、 is_nothrow_invocable、 is_nothrow_invocable_r 類別

這些範本會判斷是否型別可以叫用指定的引數類型。 `is_invocable_r` 和`is_nothrow_invocable_r`也決定是否轉換成特定類型的引動過程的結果。 `is_nothrow_invocable` 和`is_nothrow_invocable_r`也會決定是否叫用已知不會擲回例外狀況。 在 C + + 17 中新增。

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

*Callable*<br/>
要查詢的可呼叫類型。

*Args*<br/>
若要查詢引數類型。

*Convertible*<br/>
型別結果的*Callable*必須可轉換成。

## <a name="remarks"></a>備註

`is_invocable`型別述詞為 true，則如果可呼叫的型別*Callable*可以使用的引數叫用*Args*未評估的內容中。

`is_invocable_r`型別述詞為 true，則如果可呼叫的型別*Callable*可以使用的引數叫用*引數*中的未評估的內容，來產生結果的型別可轉換為*可轉換*。

`is_nothrow_invocable`型別述詞為 true，則如果可呼叫的型別*Callable*可以使用的引數叫用*Args*未評估的內容中，而且這類呼叫已知不會擲回例外狀況。

`is_nothrow_invocable_r`型別述詞為 true，則如果可呼叫的型別*Callable*可以使用的引數叫用*引數*中的未評估的內容，來產生結果的型別可轉換為*可轉換*，和，這類呼叫已知不會擲回例外狀況。

每個型別*可轉換*， *Callable*，和參數封裝中的型別*引數*必須是完整的型別、 未知的繫結的陣列或可能是 cv 限定**void**。 否則，述詞的行為未定義。

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

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)<br/>

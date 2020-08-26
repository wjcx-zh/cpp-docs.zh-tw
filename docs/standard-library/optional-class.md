---
title: 選用類別
ms.date: 11/04/2016
f1_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
helpviewer_keywords:
- optional/std::optional
- optional/std::optional::has_value
- optional/std::optional::reset
- optional/std::optional::value
- optional/std::optional::value_or
ms.openlocfilehash: b1e77325cc485da1caec91316ce5d46cfa6357dc
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841931"
---
# <a name="optional-class"></a>選用類別

類別樣板 `optional<T>` 描述的物件不一定會包含類型的值，也 `T` 稱為 *包含的值*。

當的實例 `optional<T>` 包含值時，會在物件的儲存體內配置包含的值 `optional` ，該區域會在適當對齊類型的區域內進行配置 `T` 。 當轉換為時 `optional<T>` **`bool`** ， **`true`** 如果物件包含值，則結果為，否則為 **`false`** 。

包含的物件類型 `T` 不得 [in_place_t](in-place-t-struct.md) 或 [nullopt_t](nullopt-t-structure.md)。 `T` 必須是 *易損壞*，也就是它的函式必須回收所有擁有的資源，而且可能不會擲回任何例外狀況。

`optional`類別是 c + + 17 的新類別。

## <a name="syntax"></a>語法

```cpp
template <class T>
class optional
{
    using value_type = T;
};

template<class T> optional(T) -> optional<T>;
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
| **函數和函式** | |
|[選](#optional) | 建構類型 `optional` 的物件。 |
|[~ 選擇性](#optional-destructor) | 終結型別的物件 `optional` 。 |
| **指派** | |
| [運算子 =](#op_eq) | `optional`以另一個複本取代 `optional` 。 |
| [emplace](#op_eq) | 使用指定的引數，初始化包含的值。 |
| **交換** | |
| [交換](#swap) | 以另一個值交換包含的值或空白狀態 `optional` 。 |
| **觀察者** | |
| [has_value](#has_value) | 傳回物件是否 `optional` 包含值。 |
| [value](#value) | 傳回包含的值。 |
| [value_or](#value_or) | 傳回包含的值，如果不存在任何值，則傳回替代選項。 |
| [運算子->](#op_as) | 參考物件的包含值 `optional` 。 |
| [運算子](#op_mem) | 參考物件的包含值 `optional` 。 |
| [運算子 bool](#op_bool) | 傳回物件是否 `optional` 包含值。 |
| **修飾詞** | |
| [reset](#reset) | 藉 `optional` 由終結任何包含的值來重設。 |

## <a name="has_value"></a><a name="has_value"></a> has_value

```cpp
constexpr bool has_value() const noexcept;
```

## <a name="optional-constructor"></a><a name="optional"></a> 選擇性的函式

建構類型 `optional` 的物件。

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t nullopt) noexcept;
constexpr optional(const optional& rhs);
constexpr optional(optional&& rhs) noexcept;

template <class... Args>
constexpr explicit optional(in_place_t, Args&&... args);

template <class U, class... Args>
constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);

template <class U = T>
explicit constexpr optional(U&& rhs);

template <class U>
explicit optional(const optional<U>& rhs);

template <class U>
explicit optional(optional<U>&& rhs);
```

### <a name="parameters"></a>參數

*rhs*\
`optional`要從中複製或移動的結構，其包含值。

*i_list*\
要從中建立包含值的初始化運算式清單。

*參數*\
要從中建立包含值的引數清單。

### <a name="remarks"></a>備註

`constexpr optional() noexcept;`
`constexpr optional(nullopt_t nullopt) noexcept;` 這些函式 `optional` 會建立不包含值的。

`constexpr optional(const optional& rhs);` 複製函式會從引數包含的值初始化包含的值。 除非是 true，否則會定義為 **deleted** `is_copy_constructible_v<T>` ，而且如果是 true，則會很簡單 `is_trivially_copy_constructible_v<T>` 。

`constexpr optional(optional&& rhs) noexcept;` 移動的函式會從引數的包含值中移動，以初始化包含的值。 除非是 true，否則它不會參與多載解析 `is_move_constructible_v<T>` ，而且如果是 true，則會很簡單 `is_trivially_move_constructible_v<T>` 。

`template <class... Args> constexpr explicit optional(in_place_t, Args&&... args);` 直接初始化包含的值，就像使用引數一樣 `std::forward<Args>(args)` 。 **`constexpr`** 如果所使用的函式是，則此為函數 `T` **`constexpr`** 。 除非為 true，否則它不會參與多載解析 `is_constructible_v<T, Args...>` 。

`template <class U, class... Args> constexpr explicit optional(in_place_t, initializer_list<U> i_list, Args&&... args);` 直接初始化包含的值，就像使用引數一樣 `i_list, std::forward<Args>(args)` 。 **`constexpr`** 如果所使用的函式是，則此為函數 `T` **`constexpr`** 。 除非為 true，否則它不會參與多載解析 `is_constructible_v<T, initializer_list<U>&, Args&&...>` 。

`template <class U = T> explicit constexpr optional(U&& rhs);` 直接初始化包含的值，就像使用一樣 `std::forward<U>(v)` 。 **`constexpr`** 如果所使用的函式是，則此為函數 `T` **`constexpr`** 。 它不會參與多載解析 `is_constructible_v<T, U&&>` ，除非是 true，而且 `is_same_v<remove_cvref_t<U>, in_place_t>` 和為 `is_same_v<remove_cvref_t<U>, optional>` false。

`template <class U> explicit optional(const optional<U>& rhs);` 如果 *rhs* 包含值，則直接從引數包含的值初始化包含的值。 它不會參與多載解析，除非是 true、、、、、、、 `is_constructible_v<T, const U&>` `is_constructible_v<T, optional<U>&>` `is_constructible_v<T, optional<U>&&>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>` `is_convertible_v<optional<U>&, T>` `is_convertible_v<optional<U>&&, T>` `is_convertible_v<const optional<U>&, T>` 和 `is_convertible_v<const optional<U>&&, T>` 都是 false。

`template <class U> explicit optional(optional<U>&& rhs);` 如果 *rhs* 包含值，則直接初始化包含的值，就像使用一樣 `std::move(*rhs)` 。 它不會參與多載解析，除非是 true、、、、、、、 `is_constructible_v<T, U&&>` `is_constructible_v<T, optional<U>&>` `is_constructible_v<T, optional<U>&&>` `is_constructible_v<T, const optional<U>&>` `is_constructible_v<T, const optional<U>&&>` `is_convertible_v<optional<U>&, T>` `is_convertible_v<optional<U>&&, T>` `is_convertible_v<const optional<U>&, T>` 和 `is_convertible_v<const optional<U>&&, T>` 都是 false。

## <a name="optional-destructor"></a><a name="optional-destructor"></a> ~ 選擇性的函式

藉由叫用其函式，終結任何非完整易損壞包含的值（如果有的話）。

```cpp
~optional();
```

### <a name="remarks"></a>備註

如果 `T` 是完整易損壞，則 `optional<T>` 也會完整易損壞。

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

以複本取代包含的值， `optional` 或從另一個包含的 `optional` 值進行移動。

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional& rhs);
optional& operator=(optional&&) noexcept( /* see below */ );

template <class U = T>
    optional& operator=(U&&);

template <class U>
optional& operator=(const optional<U>&);

template <class U>
    optional& operator=(optional<U>&&);

template <class... Args>
T& emplace(Args&&...);

template <class U, class... Args>
T& emplace(initializer_list<U>, Args&&...);
```

## <a name="operator-"></a><a name="op_as"></a> 運算子->

取值物件的包含值 `optional` 。

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

## <a name="operator"></a><a name="op_mem"></a> 運算子

取值物件的包含值 `optional` 。

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

## <a name="operator-bool"></a><a name="op_bool"></a> 運算子 bool

報告物件是否 `optional` 有包含的值。

```cpp
constexpr explicit operator bool() const noexcept;
```

## <a name="reset"></a><a name="reset"></a> 重 置

實際上，會呼叫包含物件的函式（如果有的話），並將它設定為未初始化的狀態。

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a> 交換

```cpp
template<class T>
void swap(optional<T>&, optional<T>&) noexcept;
```

## <a name="value"></a><a name="value"></a> 值

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

## <a name="value_or"></a><a name="value_or"></a> value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

## <a name="see-also"></a>另請參閱

[\<optional>](optional.md)

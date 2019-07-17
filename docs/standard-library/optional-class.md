---
title: 可省略的類別
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
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: 414b3e608e915ec06dbdf90726151a1c33ea4c60
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269200"
---
# <a name="optional-class"></a>可省略的類別

描述可能會或可能不會包含值的物件。

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

|||
|-|-|
|[optional](#optional)|建構類型 `optional` 的物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[has_value](#has_value)|傳回**真**如果`optional`包含值。|
|[reset](#reset)|重設`optional`。|
|[value](#value)|評估`optional`值。|
|[value_or](#value_or)|評估`optional`值。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_eq)|會取代`optional`的另一個複本`optional`。|
|[operator->](#op_as)|將值指派給`optional`。|
|[operator*](#op_mem)|參考記憶體的`optional`。|
|[operator bool](#op_bool)|傳回布林值的`optional`值。|

### <a name="has_value"></a> has_value

```cpp
constexpr bool has_value() const noexcept;
```

### <a name="optional"></a> 選擇性

建構類型 `optional` 的物件。 也包含解構函式。

```cpp
constexpr optional() noexcept;
constexpr optional(nullopt_t) noexcept;
constexpr optional(const optional&);
constexpr optional(optional&&) noexcept(see below);

template <class... Args>
    constexpr explicit optional(in_place_t, Args&&...);
template <class U, class... Args>
    constexpr explicit optional(in_place_t, initializer_list<U>, Args&&...);
template <class U = T>
    explicit constexpr optional(U&&);
template <class U>
    explicit optional(const optional<U>&);
template <class U>
    explicit optional(optional<U>&&);

~optional();
```

### <a name="op_eq"></a> 運算子 =

會取代`optional`的另一個複本`optional`。

```cpp
optional& operator=(nullopt_t) noexcept;
optional& operator=(const optional&);
optional& operator=(optional&&) noexcept(see below);

template <class U = T>
    optional& operator=(U&&); template <class U> optional& operator=(const optional<U>&);
template <class U>
    optional& operator=(optional<U>&&); template <class... Args> T& emplace(Args&&...);
template <class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
```

### <a name="op_as"></a> operator->

```cpp
constexpr const T* operator->() const;
constexpr T* operator->();
```

### <a name="op_mem"></a> 運算子 *

```cpp
constexpr const T& operator*() const&;
constexpr T& operator*() &;
constexpr T&& operator*() &&;
constexpr const T&& operator*() const&&;
```

### <a name="op_bool"></a> 運算子 bool

```cpp
constexpr explicit operator bool() const noexcept;
```

### <a name="reset"></a> 重設

```cpp
void reset() noexcept;
```

### <a name="value"></a> 值

```cpp
constexpr const T& value() const&;
constexpr T& value() &;
constexpr T&& value() &&;
constexpr const T&& value() const&&;
```

### <a name="value_or"></a> value_or

```cpp
template <class U>
    constexpr T value_or(U&&) const&;
template <class U>
    constexpr T value_or(U&&) &&;
```

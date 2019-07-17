---
title: variant 類別
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
helpviewer_keywords:
- variant/std::variant
- variant/std::variant::emplace
- variant/std::variant::index
- variant/std::variant::valueless_by_exception
ms.openlocfilehash: 9bfdf644374a0b825fd0ca02bf4164a766cb42a3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269300"
---
# <a name="variant-class"></a>variant 類別

在任何指定時間的變任何的體執行個體可能存有值的其中一個替代的類型，或者它會保留任何值。

## <a name="syntax"></a>語法

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[Variant](#variant)|建構類型 `variant` 的物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[emplace](#emplace)|建立包含新的值。|
|[index](#index)|傳回包含值的索引。|
|[swap](#swap)||
|[valueless_by_exception](#emplace)|傳回**false**如果 variant 包含的值。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_eq)|以另一個變數的複本取代變數。|

## <a name="emplace"></a> emplace

建立包含新的值。

```cpp
template <class T, class... Args>
    T& emplace(Args&&...);
template <class T, class U, class... Args>
    T& emplace(initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(Args&&...);
template <size_t I, class U, class... Args>
    variant_alternative_t<I, variant<Types...>>& emplace(initializer_list<U>, Args&&...);
```

## <a name="index"></a> 索引

傳回包含值的索引。

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a> Variant

建構類型 `variant` 的物件。 也包含解構函式。

```cpp
constexpr variant() noexcept(see below);
variant(const variant&);
variant(variant&&) noexcept(see below);
template <class T>
    constexpr variant(T&&) noexcept(see below);
template <class T, class... Args>
    constexpr explicit variant(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    constexpr explicit variant(in_place_type_t<T>, initializer_list<U>, Args&&...);
template <size_t I, class... Args>
    constexpr explicit variant(in_place_index_t<I>, Args&&...);
template <size_t I, class U, class... Args>
    constexpr explicit variant(in_place_index_t<I>, initializer_list<U>, Args&&...);

template <class Alloc>
    variant(allocator_arg_t, const Al&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, const variant&);
template <class Alloc>
    variant(allocator_arg_t, const Al&, variant&&);
template <class Alloc, class T>
    variant(allocator_arg_t, const Al&, T&&);
template <class Alloc, class T, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, Args&&...);
template <class Alloc, class T, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_type_t<T>, initializer_list<U>, Args&&...);
template <class Alloc, size_t I, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, Args&&...);
template <class Alloc, size_t I, class U, class... Args>
    variant(allocator_arg_t, const Al&, in_place_index_t<I>, initializer_list<U>, Args&&...);

~variant();
```

### <a name="parameters"></a>參數

*Al*\
搭配這個物件使用的配置器類別。

## <a name="op_eq"></a> 運算子 =

以另一個變數的複本取代變數。

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a> 交換

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless"></a> valueless_by_exception

傳回**false**如果 variant 包含的值。

```cpp
constexpr bool valueless_by_exception() const noexcept;
```

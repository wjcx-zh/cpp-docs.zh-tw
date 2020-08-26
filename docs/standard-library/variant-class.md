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
ms.openlocfilehash: aba121604636ebd253523acb9b630dd9ab762584
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840020"
---
# <a name="variant-class"></a>variant 類別

任何指定時間內的任何變異實例都會保留其中一個替代類型的值，或不包含任何值。

## <a name="syntax"></a>語法

```cpp
template <class... Types>
    class variant
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[variant](#variant)|建構類型 `variant` 的物件。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[emplace](#emplace)|建立新的包含值。|
|[index](#index)|傳回包含值的索引。|
|[交換](#swap)||
|[valueless_by_exception](#emplace)|**`false`** 如果變數保留值，則傳回。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#op_eq)|以另一個變體的複本取代 variant。|

## <a name="emplace"></a><a name="emplace"></a> emplace

建立新的包含值。

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

## <a name="index"></a><a name="index"></a> 指數

傳回包含值的索引。

```cpp
constexpr size_t index() const noexcept;
```

## <a name="variant"></a><a name="variant"></a> 變異

建構類型 `variant` 的物件。 也包含一個函式。

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

*鋁*\
搭配這個物件使用的配置器類別。

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

以另一個變體的複本取代 variant。

```cpp
variant& operator=(const variant&);
variant& operator=(variant&&) noexcept(see below);
template <class T>
    variant& operator=(T&&) noexcept(see below);
```

## <a name="swap"></a><a name="swap"></a> 交換

```cpp
void swap(variant&) noexcept(see below);
```

## <a name="valueless_by_exception"></a><a name="valueless"></a> valueless_by_exception

**`false`** 如果變數保留值，則傳回。

```cpp
constexpr bool valueless_by_exception() const noexcept;
```

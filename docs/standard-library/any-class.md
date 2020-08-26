---
title: 任何類別
ms.date: 04/04/2019
f1_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
helpviewer_keywords:
- any/std::any
- any/std::any::emplace
- any/std::any::has_value
- any/std::any::reset
- any/std::any::swap
- any/std::any::type
ms.openlocfilehash: defec0f6ab8f59219afddcefc67ea93435347978
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844739"
---
# <a name="any-class"></a>任何類別

儲存任何符合函式需求之類型的實例，或沒有任何值，稱為類別的任何物件狀態。

儲存的實例稱為包含的值。 如果兩個狀態都沒有值，或兩者都有值，且包含的值相同，則兩者都相同。

## <a name="syntax"></a>語法

```cpp
class any
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[任意](#any)|建構類型 `any` 的物件。|

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[emplace](#emplace)|設定任何值。|
|[has_value](#has_value)|**`true`** 如果有任何值，則傳回。|
|[reset](#reset)|重設為 any。|
|[交換](#swap)|交換兩個物件。|
|[type](#type)|傳回任何型別。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 =](#op_eq)|以另一個複本的複本取代 any。|

## <a name="any"></a><a name="any"></a> 任何

建構類型 `any` 的物件。 也包含一個函式。

```cpp
constexpr any() noexcept;
any(const any& other);
any(any&& other) noexcept;
template <class T>
    any(T&& value);
template <class T, class... Args>
    explicit any(in_place_type_t<T>, Args&&...);
template <class T, class U, class... Args>
    explicit any(in_place_type_t<T>, initializer_list<U>, Args&&...);

~any();
```

## <a name="emplace"></a><a name="emplace"></a> emplace

設定任何值。

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a><a name="has_value"></a> has_value

**`true`** 如果有任何值，則傳回。

```cpp
bool has_value() const noexcept;
```

## <a name="operator"></a><a name="op_eq"></a> 運算子 =

以另一個複本的複本取代 any。

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>參數

*對*\
要複製到任何的。

## <a name="reset"></a><a name="reset"></a> 重 置

重設為 any。

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a> 交換

交換兩個物件。

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a><a name="type"></a> 類型

傳回任何型別。

```cpp
const type_info& type() const noexcept;
```

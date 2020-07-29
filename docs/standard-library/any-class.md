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
ms.openlocfilehash: 66e74a7fa7f35aae9ac9e1f3ba7520e8d3f9b3f2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203958"
---
# <a name="any-class"></a>任何類別

儲存符合函式需求的任何類型實例，或沒有任何值，這稱為類別的任何物件的狀態。

預存的實例稱為包含的值。 如果兩個狀態都沒有值，或兩者都具有值，且包含的值相同，則兩者都相同。

## <a name="syntax"></a>語法

```cpp
class any
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[任何](#any)|建構類型 `any` 的物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[emplace](#emplace)|設定任何值。|
|[has_value](#has_value)|**`true`** 如果有任何值，則傳回。|
|[reset](#reset)|重設任何。|
|[調換](#swap)|交換兩個物件。|
|[type](#type)|傳回任何類型。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](#op_eq)|以另一個的複本取代 any。|

## <a name="any"></a><a name="any"></a>任何

建構類型 `any` 的物件。 也包含一個析構函式。

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

## <a name="emplace"></a><a name="emplace"></a>emplace

設定任何值。

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a><a name="has_value"></a>has_value

**`true`** 如果有任何值，則傳回。

```cpp
bool has_value() const noexcept;
```

## <a name="operator"></a><a name="op_eq"></a>operator =

以另一個的複本取代 any。

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>參數

*再*\
任何複製到 any 的。

## <a name="reset"></a><a name="reset"></a>啟動

重設任何。

```cpp
void reset() noexcept;
```

## <a name="swap"></a><a name="swap"></a>調換

交換兩個物件。

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a><a name="type"></a> 類型

傳回任何類型。

```cpp
const type_info& type() const noexcept;
```

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
ms.openlocfilehash: 050276da665ab6ed3eb53d9e65bfea06b88bcbea
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268750"
---
# <a name="any-class"></a>任何類別

存放區的建構函式需求也符合任何類型的執行個體具有任何值，也就是呼叫類別的狀態的任何物件。

預存的執行個體呼叫包含的值。 如果兩者都有無任何值，或兩者都有值，而且包含的值是相同的兩個狀態都是相同的。

## <a name="syntax"></a>語法

```cpp
class any
```

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[any](#any)|建構類型 `any` 的物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[emplace](#emplace)|設定任何值。|
|[has_value](#has_value)|傳回 **，則為 true**如果任何的值。|
|[reset](#reset)|重設任何。|
|[swap](#swap)|交換兩個的任何物件。|
|[type](#type)|傳回的任何類型。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator=](#op_eq)|任何會取代任何的另一個複本。|

## <a name="any"></a> 任何

建構類型 `any` 的物件。 也包含解構函式。

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

## <a name="emplace"></a> emplace

設定任何值。

```cpp
template <class T, class... Args>
    decay_t<T>& emplace(Args&& ...);
template <class T, class U, class... Args>
    decay_t<T>& emplace(initializer_list<U>, Args&&...);
```

## <a name="has_value"></a> has_value

傳回 **，則為 true**如果任何的值。

```cpp
bool has_value() const noexcept;
```

## <a name="op_eq"></a> 運算子 =

任何會取代任何的另一個複本。

```cpp
any& operator=(const any& right);
any& operator=(any&& right) noexcept;
template <class T>
    any& operator=(T&& right);
```

### <a name="parameters"></a>參數

*權限*\
任何要複製到任何。

## <a name="reset"></a> 重設

重設任何。

```cpp
void reset() noexcept;
```

## <a name="swap"></a> 交換

交換兩個的任何物件。

```cpp
void swap(any& rhs) noexcept;
```

## <a name="type"></a> 型別

傳回的任何類型。

```cpp
const type_info& type() const noexcept;
```

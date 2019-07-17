---
title: default_delete 結構
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: e9e1fcc68539e55486f4ea27e6dd5c49bed11fdf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269260"
---
# <a name="defaultdelete-struct"></a>default_delete 結構

執行除法運算的預先定義的函式物件 (`operator/`) 在其引數。

## <a name="syntax"></a>語法

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>需求

**標頭：** \<memory>

**命名空間：** std

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|||
|-|-|
|[default_delete](#default_delete)|`default_delete` 類型物件的建構函式。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator()](#op_paren)|參考運算子，來存取`default_delete`。|

## <a name="default_delete"></a> default_delete

`default_delete` 類型物件的建構函式。

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="op_paren"></a> operator()

參考運算子，來存取`default_delete`。

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>另請參閱

[\<memory>](../standard-library/memory.md)

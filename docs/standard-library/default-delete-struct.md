---
title: default_delete 結構
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: 8baa9f5d294cf083fd55414cd529e438f328d1a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845077"
---
# <a name="default_delete-struct"></a>default_delete 結構

在其引數上執行除法運算 () 的預先定義函式物件 `operator/` 。

## <a name="syntax"></a>語法

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>規格需求

**標頭：**\<memory>

**命名空間：** std

## <a name="members"></a>成員

### <a name="constructors"></a>建構函式

|名稱|描述|
|-|-|
|[default_delete](#default_delete)|`default_delete` 類型物件的建構函式。|

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[運算子 ( # B1 ](#op_paren)|要存取的參考運算子 `default_delete` 。|

## <a name="default_delete"></a><a name="default_delete"></a> default_delete

`default_delete` 類型物件的建構函式。

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="operator"></a><a name="op_paren"></a> 運算子 ( # A1

要存取的參考運算子 `default_delete` 。

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>另請參閱

[\<memory>](../standard-library/memory.md)

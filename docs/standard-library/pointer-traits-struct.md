---
title: pointer_traits 結構
ms.date: 11/04/2016
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
- memory/std::pointer_traits::pointer_to
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
ms.openlocfilehash: 6d89348867982bfb86c0bf2404a017f6a448d1a1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687145"
---
# <a name="pointer_traits-struct"></a>pointer_traits 結構

提供 `allocator_traits` 類型之物件所需的資訊，以描述具有 `Ptr` 指標類型的配置器。

## <a name="syntax"></a>語法

```cpp
template <class Ptr>
    struct pointer_traits;
```

## <a name="remarks"></a>備註

Ptr 可以是類型 `Ty *` 的原始指標，或是具有下列屬性的類別。

```cpp
struct Ptr
{ // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj); // optional
};
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedef

|||
|-|-|
|`typedef T2 difference_type`|類型 `T2` 為 `Ptr::difference_type` (如果該類型存在)，否則為 `ptrdiff_t`。 如果 `Ptr` 為原始指標，則類型為 `ptrdiff_t`。|
|`typedef T1 element_type`|類型 `T1` 為 `Ptr::element_type` (如果該類型存在)，否則為 `Ty`。 如果 `Ptr` 為原始指標，則類型為 `Ty`。|
|`typedef Ptr pointer`|類型為 `Ptr`。|

### <a name="structs"></a>結構

|||
|-|-|
|`rebind`|嘗試將基礎指標類型轉換為指定類型。|

### <a name="methods"></a>方法

|[屬性]|描述|
|----------|-----------------|
|[pointer_to](#pointer_to)|將任意的參考轉換為 `Ptr` 類別的物件。|

### <a name="pointer_to"></a>pointer_to

傳回 `Ptr::pointer_to(obj)` 的靜態方法 (如果該函式存在)。 否則，不可能將任意參考轉換為 `Ptr` 類別的物件。 如果 `Ptr` 是原始指標，此方法會傳回 `addressof(obj)`。

```cpp
static pointer pointer_to(element_type& obj);
```

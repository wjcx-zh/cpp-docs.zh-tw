---
title: '&lt;new&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419795"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedef

## <a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>備註

這個數位是由平行線程以時態位置存取的兩個物件所佔用的最大連續記憶體大小。 至少應為 `alignof(max_align_t)`。

### <a name="example"></a>範例

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>備註

這是兩個同時存取的物件之間最小的建議位移，以避免因執行所引進的爭用而造成額外的效能降低。 至少應為 `alignof(max_align_t)`。

### <a name="example"></a>範例

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a>new_handler

此類型會指向適合用來作為新處理常式的函式。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>備註

當**operator new**或 `operator new[]` 無法滿足額外儲存空間的要求時，就會呼叫這種類型的處理常式函數。

### <a name="example"></a>範例

如需使用 [ 作為傳回值的範例，請參閱 ](../standard-library/new-functions.md#set_new_handler)set_new_handler`new_handler`。

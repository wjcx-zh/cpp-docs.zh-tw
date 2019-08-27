---
title: '&lt;new&gt; typedef'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245142"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedef

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>備註

這個數字是記憶體的建議的連續時間區域性與並行執行緒存取的兩個物件所佔用大小的最大值。 應該至少為`alignof(max_align_t)`。

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

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>備註

這個數目是兩個並行存取的物件，以避免額外的效能降低，原因是由實作所導入的爭用之間的最小建議的位移。 應該至少為`alignof(max_align_t)`。

### <a name="example"></a>範例

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

此類型會指向適合用來作為新處理常式的函式。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>備註

這種類型的處理常式函式會呼叫**new 運算子**或`operator new[]`當無法滿足的要求額外的儲存體。

### <a name="example"></a>範例

如需使用 `new_handler` 作為傳回值的範例，請參閱 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。

---
title: '&lt;memory_resource>&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269340"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource>&gt;

定義容器範本類別 memory_resource> 和其支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <memory_resource>
```

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|測試運算子左邊的 memory_resource> 物件是否不等於右邊的 memory_resource> 物件。|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|測試運算子左邊的 memory_resource> 物件等於右邊的 memory_resource> 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>函式

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>類別和結構

|||
|-|-|
|[memory_resource> 類別](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource 類別](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options 結構](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource 類別](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource 類別](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>

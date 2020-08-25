---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: de88feb691d0ec1bc9bf9b9dc2bc40cbc31a1cfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831043"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource&gt;

定義容器類別範本 memory_resource 及其支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <memory_resource>
```

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|名稱|描述|
|-|-|
|[operator！ =](../standard-library/memory-resource-operators.md#op_neq)|測試運算子左邊的 memory_resource 物件，是否不等於右邊的 memory_resource 物件。|
|[operator = =](../standard-library/memory-resource-operators.md#op_eq_eq)|測試運算子左邊的 memory_resource 物件是否相等於右邊的 memory_resource 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|名稱|描述|
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Functions

|名稱|描述|
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>類別和結構

|名稱|描述|
|-|-|
|[memory_resource 類別](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource 類別](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options 結構](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource 類別](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource 類別](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)

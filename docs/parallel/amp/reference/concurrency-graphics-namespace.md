---
title: Concurrency::graphics 命名空間
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 942b3bbace85fa297bba6cd4b509f67006a4aed3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226733"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空間

圖形命名空間提供的類型和函式是針對圖形程式設計所設計。

## <a name="syntax"></a>語法

```cpp
namespace graphics;
```

## <a name="members"></a>成員

### <a name="namespaces"></a>命名空間

|Name|說明|
|----------|-----------------|
|[Concurrency：： graphics：:d irect3d 命名空間](concurrency-graphics-direct3d-namespace.md)|提供 Direct3D interop 的功能。|

### <a name="typedefs"></a>Typedefs

|Name|說明|
|----------|-----------------|
|`uint`|[Uint_2 類別](uint-2-class.md)、 [uint_3 類別](uint-3-class.md)和[uint_4 類別](uint-4-class.md)的元素類型。 定義為 `typedef unsigned int uint;`。|

### <a name="enumerations"></a>列舉

|Name|說明|
|----------|-----------------|
|[Address_mode 列舉](concurrency-graphics-namespace-enums.md#address_mode)。|指定材質取樣支援的位址模式。|
|[filter_mode 列舉](concurrency-graphics-namespace-enums.md#filter_mode)|指定支援材質取樣的篩選模式。|

### <a name="classes"></a>類別

|Name|說明|
|----------|-----------------|
|[材質類別](texture-class.md)|材質是範圍定義域中 accelerator_view 的資料匯總。 它是變數的集合，範圍定義域中的每個元素各一個。 每個變數都包含一個對應至 c + + 基本型別（不帶正負號的 int、int、float、double）或純量型別標準的值，或 unorm （定義于 concurrency：： graphics），或 concurrency：： graphics 中定義的合格短向量型別。|
|[writeonly_texture_view 類別](writeonly-texture-view-class.md)|Writeonly_texture_view 提供材質的 writeonly 存取權。|
|[double_2 類別](double-2-class.md)|表示2個值的短向量 **`double`** 。|
|[double_3 類別](double-3-class.md)|代表3個值的短向量 **`double`** 。|
|[double_4 類別](double-4-class.md)|代表4個值的短向量 **`double`** 。|
|[float_2 類別](float-2-class.md)|表示2個值的短向量 **`float`** 。|
|[float_3 類別](float-3-class.md)|代表3個值的短向量 **`float`** 。|
|[float_4 類別](float-4-class.md)|代表4個值的短向量 **`float`** 。|
|[int_2 類別](int-2-class.md)|表示2個值的短向量 **`int`** 。|
|[int_3 類別](int-3-class.md)|代表3個值的短向量 **`int`** 。|
|[int_4 類別](int-4-class.md)|代表4個值的短向量 **`int`** 。|
|[norm_2 類別](norm-2-class.md)|表示2個值的短向量 `norm` 。|
|[norm_3 類別](norm-3-class.md)|代表3個值的短向量 `norm` 。|
|[norm_4 類別](norm-4-class.md)|代表4個值的短向量 `norm` 。|
|[uint_2 類別](uint-2-class.md)|表示2個值的短向量 `uint` 。|
|[uint_3 類別](uint-3-class.md)|代表3個值的短向量 `uint` 。|
|[uint_4 類別](uint-4-class.md)|代表4個值的短向量 `uint` 。|
|[unorm_2 類別](unorm-2-class.md)|表示2個值的短向量 `unorm` 。|
|[unorm_3 類別](unorm-3-class.md)|代表3個值的短向量 `unorm` 。|
|[unorm_4 類別](unorm-4-class.md)|代表4個值的短向量 `unorm` 。|
|[取樣器類別](sampler-class.md)|表示用於材質取樣的取樣器設定。|
|[short_vector 結構](short-vector-structure.md)|提供值之短向量的基本實作為。|
|[short_vector_traits 結構](short-vector-traits-structure.md)|提供用來抓取短向量的長度和類型。|
|[texture_view 類別](texture-view-class.md)|提供材質的讀取存取和寫入權限。|

### <a name="functions"></a>函式

|Name|說明|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|已多載。 將來源材質的內容複寫到目的地主機緩衝區。|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|已多載。 以非同步方式將來源材質的內容複寫到目的地主機緩衝區。|

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間（C++ AMP）](concurrency-namespace-cpp-amp.md)

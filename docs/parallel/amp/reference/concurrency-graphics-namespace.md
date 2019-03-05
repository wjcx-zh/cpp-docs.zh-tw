---
title: Concurrency::graphics 命名空間
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: ef61c93e062b375377a0afe62aa7f622f6c0d4ac
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326528"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空間

圖形命名空間提供型別和函數專為圖形程式設計所設計。

## <a name="syntax"></a>語法

```
namespace graphics;
```

## <a name="members"></a>成員

### <a name="namespaces"></a>命名空間

|名稱|描述|
|----------|-----------------|
|[Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)|提供 Direct3D interop 的函式。|

### <a name="typedefs"></a>Typedefs

|名稱|描述|
|----------|-----------------|
|`uint`|項目類型[uint_2 類別](uint-2-class.md)， [uint_3 類別](uint-3-class.md)，並[uint_4 類別](uint-4-class.md)。 定義為`typedef unsigned int uint;`。|

### <a name="enumerations"></a>列舉

|名稱|描述|
|----------|-----------------|
|[address_mode 列舉](concurrency-graphics-namespace-enums.md#address_mode)。|指定支援的材質取樣位址模式。|
|[filter_mode 列舉](concurrency-graphics-namespace-enums.md#filter_mode)|指定材質取樣支援的篩選模式。|

### <a name="classes"></a>類別

|名稱|描述|
|----------|-----------------|
|[texture 類別](texture-class.md)|材質是在範圍內 accelerator_view 上彙總資料。 它是變數，每個項目，對應範圍網域中的集合。 每個變數會保存為對應到 c + + 基本類型 (不帶正負號的 int、 int、 float、 double)，或純量類型範數或 unorm （定義於 concurrency:: graphics） 或合適短向量類型定義於 concurrency:: graphics。|
|[writeonly_texture_view 類別](writeonly-texture-view-class.md)|Writeonly_texture_view 提供 writeonly 存取材質。|
|[double_2 類別](double-2-class.md)|代表 2 的短向量`double`值。|
|[double_3 類別](double-3-class.md)|表示短向量的 3`double`值。|
|[double_4 類別](double-4-class.md)|代表 4 短向量`double`值。|
|[float_2 類別](float-2-class.md)|代表 2 的短向量`float`值。|
|[float_3 類別](float-3-class.md)|表示短向量的 3`float`值。|
|[float_4 類別](float-4-class.md)|代表 4 短向量`float`值。|
|[int_2 類別](int-2-class.md)|代表 2 的短向量`int`值。|
|[int_3 類別](int-3-class.md)|表示短向量的 3`int`值。|
|[int_4 類別](int-4-class.md)|代表 4 短向量`int`值。|
|[norm_2 類別](norm-2-class.md)|代表 2 的短向量`norm`值。|
|[norm_3 類別](norm-3-class.md)|表示短向量的 3`norm`值。|
|[norm_4 類別](norm-4-class.md)|代表 4 短向量`norm`值。|
|[uint_2 類別](uint-2-class.md)|代表 2 的短向量`uint`值。|
|[uint_3 類別](uint-3-class.md)|表示短向量的 3`uint`值。|
|[uint_4 類別](uint-4-class.md)|代表 4 短向量`uint`值。|
|[unorm_2 類別](unorm-2-class.md)|代表 2 的短向量`unorm`值。|
|[unorm_3 類別](unorm-3-class.md)|表示短向量的 3`unorm`值。|
|[unorm_4 類別](unorm-4-class.md)|代表 4 短向量`unorm`值。|
|[sampler 類別](sampler-class.md)|表示用於材質取樣的取樣器組態。|
|[short_vector 結構](short-vector-structure.md)|提供值的短向量的基本實作。|
|[short_vector_traits 結構](short-vector-traits-structure.md)|提供擷取短向量類型與長度。|
|[texture_view 類別](texture-view-class.md)|提供材質的寫入權限和讀取權限。|

### <a name="functions"></a>函式

|名稱|描述|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|多載。 將來源材質的內容複製到目的端主機緩衝區中。|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|多載。 以非同步方式將來源材質的內容複製到目的端主機緩衝區中。|

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** 並行

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

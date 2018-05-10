---
title: 'Concurrency:: graphics 命名空間 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP_GRAPHICS/Concurrency
dev_langs:
- C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2da450ca30ee780f0e493f0b120de33a939a4cd7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空間
圖形命名空間提供型別和函式針對圖形程式設計所設計。  
  
## <a name="syntax"></a>語法  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>成員  
  
### <a name="namespaces"></a>命名空間  
  
|名稱|描述|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)|Direct3D interop 提供函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`uint`|項目類型[uint_2 類別](uint-2-class.md)， [uint_3 類別](uint-3-class.md)，和[uint_4 類別](uint-4-class.md)。 定義為`typedef unsigned int uint;`。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|描述|  
|----------|-----------------|  
|[address_mode 列舉](concurrency-graphics-namespace-enums.md#address_mode)。|指定位址模式支援紋理取樣。|  
|[filter_mode 列舉](concurrency-graphics-namespace-enums.md#filter_mode)|指定支援紋理取樣的篩選模式。|  
  
### <a name="classes"></a>類別  
  
|名稱|描述|  
|----------|-----------------|  
|[texture 類別](texture-class.md)|紋理是將資料彙總上 accelerator_view 範圍網域中。 它是變數，其中每個項目範圍網域中的集合。 每個變數持有值，對應至 c + + 基本型別 (不帶正負號的 int、 int、 float、 double)，或在 concurrency:: graphics 中定義的純量型別 norm 或 unorm （定義於 concurrency:: graphics） 或符合資格的短向量類型。|  
|[writeonly_texture_view 類別](writeonly-texture-view-class.md)|Writeonly_texture_view 存取 writeonly 紋理。|  
|[double_2 類別](double-2-class.md)|代表 2 短向量`double`值。|  
|[double_3 類別](double-3-class.md)|代表 3 短向量`double`值。|  
|[double_4 類別](double-4-class.md)|代表 4 短向量`double`值。|  
|[float_2 類別](float-2-class.md)|代表 2 短向量`float`值。|  
|[float_3 類別](float-3-class.md)|代表 3 短向量`float`值。|  
|[float_4 類別](float-4-class.md)|代表 4 短向量`float`值。|  
|[int_2 類別](int-2-class.md)|代表 2 短向量`int`值。|  
|[int_3 類別](int-3-class.md)|代表 3 短向量`int`值。|  
|[int_4 類別](int-4-class.md)|代表 4 短向量`int`值。|  
|[norm_2 類別](norm-2-class.md)|代表 2 短向量`norm`值。|  
|[norm_3 類別](norm-3-class.md)|代表 3 短向量`norm`值。|  
|[norm_4 類別](norm-4-class.md)|代表 4 短向量`norm`值。|  
|[uint_2 類別](uint-2-class.md)|代表 2 短向量`uint`值。|  
|[uint_3 類別](uint-3-class.md)|代表 3 短向量`uint`值。|  
|[uint_4 類別](uint-4-class.md)|代表 4 短向量`uint`值。|  
|[unorm_2 類別](unorm-2-class.md)|代表 2 短向量`unorm`值。|  
|[unorm_3 類別](unorm-3-class.md)|代表 3 短向量`unorm`值。|  
|[unorm_4 類別](unorm-4-class.md)|代表 4 短向量`unorm`值。|  
|[sampler 類別](sampler-class.md)|代表用於紋理取樣的取樣器組態。|  
|[short_vector 結構](short-vector-structure.md)|提供值的短向量的基本實作。|  
|[short_vector_traits 結構](short-vector-traits-structure.md)|提供可擷取的長度和短向量類型。|  
|[texture_view 類別](texture-view-class.md)|提供對紋理的寫入權限和讀取權限。|  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[copy](concurrency-graphics-namespace-functions.md#copy)|多載。 將來源紋理的內容複製到目的地主機的緩衝區。|  
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|多載。 以非同步方式將來源紋理的內容複製到目的地主機的緩衝區。|  
  
## <a name="requirements"></a>需求  
 **標頭：** amp_graphics.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

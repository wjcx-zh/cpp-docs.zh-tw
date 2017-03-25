---
title: "Concurrency:: graphics 命名空間 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP_GRAPHICS/Concurrency
dev_langs:
- C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: e08a9bc52b7ce519508bb1682287e75070d341a1
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics 命名空間
圖形的命名空間提供型別和函式，可用於圖形程式設計。  
  
## <a name="syntax"></a>語法  
  
```  
namespace graphics;  
```  
  
## <a name="members"></a>Members  
  
### <a name="namespaces"></a>命名空間  
  
|名稱|說明|  
|----------|-----------------|  
|[Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)|Direct3D interop 提供函式。|  
  
### <a name="typedefs"></a>Typedef  
  
|名稱|描述|  
|----------|-----------------|  
|`uint`|項目型別[uint_2 類別](uint-2-class.md)， [uint_3 類別](uint-3-class.md)，和[uint_4 類別](uint-4-class.md)。 定義為`typedef unsigned int uint;`。|  
  
### <a name="enumerations"></a>列舉  
  
|名稱|描述|  
|----------|-----------------|  
|[address_mode 列舉](concurrency-graphics-namespace-enums.md#address_mode)。|指定位址模式支援紋理取樣。|  
|[filter_mode 列舉](concurrency-graphics-namespace-enums.md#filter_mode)|指定篩選條件模式支援紋理取樣。|  
  
### <a name="classes"></a>類別  
  
|名稱|說明|  
|----------|-----------------|  
|[texture 類別](texture-class.md)|紋理是將資料彙總上 accelerator_view 範圍網域中。 它是每個項目範圍網域中的變數集合。 每個變數會保留值，對應到 c + + 基本型別 (不帶正負號的 int、 int、 float、 double)，或在 concurrency:: graphics 中定義的純量型別 norm 或 unorm （定義於 concurrency:: graphics） 或符合資格的短向量類型。|  
|[writeonly_texture_view 類別](writeonly-texture-view-class.md)|Writeonly_texture_view 提供紋理 writeonly 存取。|  
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
|[sampler 類別](sampler-class.md)|代表用於 「 紋理取樣的取樣器組態。|  
|[short_vector 結構](short-vector-structure.md)|提供值的短向量的基本實作。|  
|[short_vector_traits 結構](short-vector-traits-structure.md)|提供可擷取的長度和短向量類型。|  
|[texture_view 類別](texture-view-class.md)|提供讀取和寫入存取權的紋理。|  
  
### <a name="functions"></a>函式  
  
|名稱|描述|  
|----------|-----------------|  
|[copy](concurrency-graphics-namespace-functions.md#copy)|多載。 將來源紋理的內容複製到目的主機的緩衝區。|  
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|多載。 以非同步方式將來源紋理的內容複製到目的主機的緩衝區。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_graphics.h  
  
 **命名空間：** 並行  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)


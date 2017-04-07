---
title: "Concurrency::graphics::direct3d 命名空間函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs:
- C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 63cf872bd5ade28115a0eac92304554f125c8dd5
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空間函式
||||  
|-|-|-|  
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>get_sampler  
 Get D3D 取樣器狀態上的介面指定對應檢視，代表指定取樣器物件。  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Av`  
 D3D 加速器檢視所建立的 D3D 取樣器狀態。  
  
 `_Sampler`  
 基礎 D3D 取樣器狀態的介面建立的取樣器物件。  
  
### <a name="return-value"></a>傳回值  
 D3D 取樣器狀態，表示指定的取樣器相對應的 IUnknown 介面指標。  
  
##  <a name="get_texture"></a>get_texture  
 取得指定基礎 Direct3D 紋理介面[紋理](texture-class.md)物件。  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
```  
  
### <a name="parameters"></a>參數  
 `value_type`  
 紋理的項目型別。  
  
 `_Rank`  
 紋理的陣序規範。  
  
 `_Texture`  
 紋理或其基礎 Direct3D 紋理介面會傳回 accelerator_view 相關聯的紋理檢視中。  
  
### <a name="return-value"></a>傳回值  
 對應至基礎紋理 Direct3D 紋理 IUnknown 介面指標。  
  
##  <a name="make_sampler"></a>make_sampler  
 建立樣本中，從 D3D 取樣器狀態的介面指標。  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_D3D_sampler`  
 若要建立之取樣器從 D3D 取樣器狀態的 IUnknown 介面指標。  
  
### <a name="return-value"></a>傳回值  
 樣本中，代表提供的 D3D 取樣器狀態。  
  
##  <a name="make_texture"></a>make_texture  
 建立[紋理](texture-class.md)物件使用指定的參數。  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,  
    _In_ IUnknown* _D3D_texture,  
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `value_type`  
 紋理中的項目類型。  
  
 `_Rank`  
 紋理的陣序規範。  
  
 `_Av`  
 D3D 加速器檢視所建立的紋理。  
  
 `_D3D_texture`  
 若要建立從紋理 D3D 紋理的 IUnknown 介面指標。  
  
 `_View_format`  
 要用來建立從這個紋理檢視的 DXGI 格式。 傳遞格式衍生 _D3D_texture 基礎格式與此範本 value_type DXGI_FORMAT_UNKNOWN （預設值）。 提供的格式必須是相容的 _D3D_texture 基礎的格式。  
  
### <a name="return-value"></a>傳回值  
 使用提供的 D3D 紋理紋理。  
  
##  <a name="msad4"></a>msad4  
 將 4 位元組參考值取值並且 8 個位元組的來源值的比較，並累積 4 加總的向量。 每個總和會對應至不同位元組對齊的參考值取值並且來源值之間的絕對差異的遮罩的總和。  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Reference`  
 參考的 4 位元組陣列中一個 uint 值  
  
 `_Source`  
 來源向量中的兩個 uint 值的 8 個位元組的陣列。  
  
 `_Accum`  
 加入遮罩總和的參考值取值並且來源值之間的絕對差異的不同位元組對齊的 4 個值的向量。  
  
### <a name="return-value"></a>傳回值  
 傳回 4 的加總的向量。 每個總和會對應至不同位元組對齊的參考值取值並且來源值之間的絕對差異的遮罩的總和。  

## <a name="requirements"></a>需求  
 **標頭︰** amp_graphics.h  
  
 **命名空間︰** Concurrency::graphics::direct3d 

## <a name="see-also"></a>另請參閱  
 [Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)


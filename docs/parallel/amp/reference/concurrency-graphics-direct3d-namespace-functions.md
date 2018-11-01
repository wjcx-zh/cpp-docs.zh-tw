---
title: Concurrency::graphics::direct3d 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 71ce23d1238d852d42687be725de8153e938d6cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464723"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空間函式

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

##  <a name="get_sampler"></a>  get_sampler

檢視，代表指定之取樣器物件，取得 D3D 取樣器狀態介面上的特定加速器。

```
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_Av*<br/>
所建立的 D3D 取樣器狀態的 D3D 加速器檢視。

*_Sampler*<br/>
取樣器物件，為其建立基礎的 D3D 取樣器狀態介面。

### <a name="return-value"></a>傳回值

對應至表示特定取樣器的 D3D 取樣器狀態 IUnknown 介面指標。

##  <a name="get_texture"></a>  get_texture

取得指定基礎 d3d 材質介面[紋理](texture-class.md)物件。

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

*value_type*<br/>
材質的元素型別。

*_Rank*<br/>
材質的順位。

*_Texture*<br/>
材質或為其傳回基礎 d3d 材質介面的 accelerator_view 相關聯的紋理檢視中。

### <a name="return-value"></a>傳回值

IUnknown 介面指標對應到基礎材質的 Direct3D 材質。

##  <a name="make_sampler"></a>  make_sampler

從 D3D 取樣器狀態介面指標建立取樣器。

```
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_D3D_sampler*<br/>
若要建立取樣器的 D3D 取樣器狀態 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

取樣器代表提供的 D3D 取樣器狀態。

##  <a name="make_texture"></a>  make_texture

會建立[紋理](texture-class.md)物件使用指定的參數。

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

*value_type*<br/>
材質中項目的類型。

*_Rank*<br/>
材質的順位。

*_Av*<br/>
所建立的材質的 D3D 加速器檢視。

*_D3D_texture*<br/>
若要建立從材質的 D3D 材質的 IUnknown 介面指標。

*_View_format*<br/>
要從此材質建立之檢視所使用的 DXGI 格式。 傳遞 DXGI_FORMAT_UNKNOWN （預設值），從 _D3D_texture 的基礎格式及此範本的 value_type 衍生格式。 提供的格式必須與 _D3D_texture 的基礎格式相容。

### <a name="return-value"></a>傳回值

使用提供的 D3D 材質的材質。

##  <a name="msad4"></a>  msad4

比較 4 位元組參考值和 8 位元組來源值，並累積 4 個總和的向量。 每個總計對應至不同位元組對齊參考值與原始值之間絕對差異的遮罩總計。

```
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>參數

*（_r)*<br/>
一個 uint 值的 4 位元組參考陣列

*_Source*<br/>
兩個 uint 值的向量中的 8 位元組來源陣列。

*_Accum*<br/>
要加入至不同位元組對齊參考值與原始值之間絕對差異的遮罩總計的 4 個值的向量。

### <a name="return-value"></a>傳回值

傳回 4 個總和的向量。 每個總計對應至不同位元組對齊參考值與原始值之間絕對差異的遮罩總計。

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** Concurrency::graphics::direct3d

## <a name="see-also"></a>另請參閱

[Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)

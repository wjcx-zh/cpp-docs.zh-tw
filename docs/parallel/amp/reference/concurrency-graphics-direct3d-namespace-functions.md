---
title: Concurrency::graphics::direct3d 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 330c1aa94b1d122901fc23576686032400249d31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376382"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空間函式

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[姆薩德4](#msad4)|

## <a name="get_sampler"></a><a name="get_sampler"></a>get_sampler

獲取表示指定採樣器物件的給定加速器視圖上的 D3D 採樣器狀態介面。

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要創建 D3D 採樣器狀態的 D3D 加速器檢視。

*_Sampler*<br/>
為其創建基礎 D3D 採樣器狀態介面的採樣器物件。

### <a name="return-value"></a>傳回值

I未知介面指針對應於表示給定採樣器的 D3D 採樣器狀態。

## <a name="get_texture"></a><a name="get_texture"></a>get_texture

獲取指定[紋理](texture-class.md)物件基礎的 Direct3D 紋理介面。

```cpp
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
紋理的元素類型。

*_Rank*<br/>
紋理的排名。

*_Texture*<br/>
與返回基礎 Direct3D 紋理介面accelerator_view關聯的紋理或紋理視圖。

### <a name="return-value"></a>傳回值

I未知介面指針對應於紋理基礎的 Direct3D 紋理。

## <a name="make_sampler"></a><a name="make_sampler"></a>make_sampler

從 D3D 採樣器狀態介面指標創建採樣器。

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_D3D_sampler*<br/>
D3D 採樣器狀態的 I 未知介面指標,用於從中創建採樣器。

### <a name="return-value"></a>傳回值

採樣器表示提供的 D3D 採樣器狀態。

## <a name="make_texture"></a><a name="make_texture"></a>make_texture

使用指定的參數創建[紋理](texture-class.md)物件。

```cpp
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
紋理中元素的類型。

*_Rank*<br/>
紋理的排名。

*_Av*<br/>
要在其中創建紋理的 D3D 快速鍵檢視。

*_D3D_texture*<br/>
D3D 紋理的 I 未知介面指標,用於從中創建紋理。

*_View_format*<br/>
用於使用此紋理創建的檢視的 DXGI 格式。 通過DXGI_FORMAT_UNKNOWN(預設值)從_D3D_texture的基礎格式和value_type派生格式。 提供的格式必須與_D3D_texture的基礎格式相容。

### <a name="return-value"></a>傳回值

使用提供的 D3D 紋理的紋理。

## <a name="msad4"></a><a name="msad4"></a>姆薩德4

比較 4 位元組參考值和 8 位元組源值,並累積 4 個總和的向量。 每個總和對應於參考值和源值之間不同位元組對齊的絕對差異的蒙版總和。

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>參數

*_Reference*<br/>
uint 值中 4 個字節的引用陣列

*_Source*<br/>
在兩個 uint 值的向量中 8 個字節的源陣組。

*_Accum*<br/>
要添加到參考值和源值之間不同位元組對齊的掩蔽絕對差異的4個值的向量。

### <a name="return-value"></a>傳回值

返回4個總和的向量。 每個總和對應於參考值和源值之間不同位元組對齊的絕對差異的蒙版總和。

## <a name="requirements"></a>需求

**標題:** amp_graphics.h

**命名空間:** 併發::圖形::direct3d

## <a name="see-also"></a>另請參閱

[併發::圖形::direct3d命名空間](concurrency-graphics-direct3d-namespace.md)

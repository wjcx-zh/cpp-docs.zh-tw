---
title: Concurrency::graphics::direct3d 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 665732700ee6b85425f332a0eb96a5b75864a74e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126964"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空間函式

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a>get_sampler

取得指定的快速鍵對應上的 D3D 取樣器狀態介面，其代表指定的取樣器物件。

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_Av*<br/>
要在其上建立 D3D 取樣器狀態的 D3D 加速器視圖。

*_Sampler*<br/>
建立基礎 D3D 取樣器狀態介面的取樣器物件。

### <a name="return-value"></a>傳回值

IUnknown 介面指標，對應于表示給定取樣器的 D3D 取樣器狀態。

## <a name="get_texture"></a>get_texture

取得以指定之[材質](texture-class.md)物件為基礎的 Direct3D 材質介面。

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
材質的元素類型。

*_Rank*<br/>
材質的順位。

*_Texture*<br/>
與所傳回基礎 Direct3D 材質介面的 accelerator_view 相關聯的材質或材質視圖。

### <a name="return-value"></a>傳回值

IUnknown 介面指標，對應于材質基礎的 Direct3D 材質。

## <a name="make_sampler"></a>make_sampler

從 D3D 取樣器狀態介面指標建立取樣器。

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_D3D_sampler*<br/>
要從中建立取樣器之 D3D 取樣器狀態的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

取樣器代表提供的 D3D 取樣器狀態。

## <a name="make_texture"></a>make_texture

使用指定的參數建立[材質](texture-class.md)物件。

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
材質中元素的類型。

*_Rank*<br/>
材質的順位。

*_Av*<br/>
要在其上建立材質的 D3D 加速器視圖。

*_D3D_texture*<br/>
要從中建立材質之 D3D 材質的 IUnknown 介面指標。

*_View_format*<br/>
要用於從這個材質建立之視圖的 DXGI 格式。 傳遞 DXGI_FORMAT_UNKNOWN （預設值），從 _D3D_texture 的基礎格式和此範本的 value_type 衍生格式。 提供的格式必須與 _D3D_texture 的基礎格式相容。

### <a name="return-value"></a>傳回值

使用所提供 D3D 材質的材質。

## <a name="msad4"></a>msad4

比較4個位元組的參考值和8個位元組的來源值，並累計4個總和的向量。 每個總和都會對應至參考值與來源值之間不同位元組對齊之絕對差異的遮罩總和。

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>參數

*_Reference*<br/>
一個 uint 值中4個位元組的參考陣列

*_Source*<br/>
兩個 uint 值向量中8個位元組的來源陣列。

*_Accum*<br/>
4個值的向量，要加入至參考值與來源值之間不同位元組對齊的遮罩總和。

### <a name="return-value"></a>傳回值

傳回4加總的向量。 每個總和都會對應至參考值與來源值之間不同位元組對齊之絕對差異的遮罩總和。

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** Concurrency：： graphics：:d irect3d

## <a name="see-also"></a>另請參閱

[Concurrency::graphics::direct3d 命名空間](concurrency-graphics-direct3d-namespace.md)

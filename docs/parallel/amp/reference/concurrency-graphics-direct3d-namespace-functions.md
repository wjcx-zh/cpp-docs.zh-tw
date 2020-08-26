---
title: Concurrency::graphics::direct3d 命名空間函式
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 66db1d348c6c58a9226322b51662ef7a4ef75b3d
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841291"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d 命名空間函式

:::row:::
   :::column span="":::
      [`get_sampler`](#get_sampler)\
      [`get_texture`](#get_texture)
   :::column-end:::
   :::column span="":::
      [`make_sampler`](#make_sampler)
   :::column-end:::
   :::column span="":::
      [`make_texture`](#make_texture)
   :::column-end:::
   :::column span="":::
      [`msad4`](#msad4)
   :::column-end:::
:::row-end:::

## <a name="get_sampler"></a><a name="get_sampler"></a> get_sampler

取得代表指定取樣器物件之指定加速器視圖上的 D3D 取樣器狀態介面。

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_Av*<br/>
D3d 加速器視圖，要在其上建立 D3D 取樣器狀態。

*_Sampler*<br/>
建立基礎 D3D 取樣器狀態介面的取樣器物件。

### <a name="return-value"></a>傳回值

IUnknown 介面指標，對應至代表指定取樣器的 D3D 取樣器狀態。

## <a name="get_texture"></a><a name="get_texture"></a> get_texture

取得指定之 [材質](texture-class.md) 物件基礎的 Direct3D 材質介面。

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
與基礎 Direct3D 材質介面所傳回之 accelerator_view 相關聯的材質或材質視圖。

### <a name="return-value"></a>傳回值

IUnknown 介面指標，對應至材質基礎的 Direct3D 紋理。

## <a name="make_sampler"></a><a name="make_sampler"></a> make_sampler

從 D3D 取樣器狀態介面指標建立取樣器。

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>參數

*_D3D_sampler*<br/>
要從中建立取樣器之 D3D 取樣器狀態的 IUnknown 介面指標。

### <a name="return-value"></a>傳回值

取樣器代表提供的 D3D 取樣器狀態。

## <a name="make_texture"></a><a name="make_texture"></a> make_texture

使用指定的參數建立 [紋理](texture-class.md) 物件。

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
材質中的元素類型。

*_Rank*<br/>
材質的順位。

*_Av*<br/>
要在其上建立材質的 D3D 加速器視圖。

*_D3D_texture*<br/>
要從中建立材質之 D3D 材質的 IUnknown 介面指標。

*_View_format*<br/>
要用於從此材質建立之視圖的 DXGI 格式。 傳遞 DXGI_FORMAT_UNKNOWN (預設) ，從 _D3D_texture 的基礎格式和此範本的 value_type 衍生格式。 提供的格式必須與 _D3D_texture 的基礎格式相容。

### <a name="return-value"></a>傳回值

使用所提供之 D3D 材質的材質。

## <a name="msad4"></a><a name="msad4"></a> msad4

比較4位元組的參考值和8位元組的來源值，並累積4加總的向量。 每個總和都對應于參考值與來源值之間不同位元組對齊的遮罩加總。

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
四個值的向量，要加入至參考值與來源值之間不同位元組對齊的遮罩加總。

### <a name="return-value"></a>傳回值

傳回4加總的向量。 每個總和都對應于參考值與來源值之間不同位元組對齊的遮罩加總。

## <a name="requirements"></a>規格需求

**標頭：** amp_graphics。h

**命名空間：** Concurrency：： graphics：:d irect3d

## <a name="see-also"></a>另請參閱

[Concurrency：： graphics：:d irect3d 命名空間](concurrency-graphics-direct3d-namespace.md)

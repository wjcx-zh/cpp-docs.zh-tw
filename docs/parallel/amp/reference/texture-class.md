---
title: texture 類別
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: b8a37293166ec21aeb9410f05fb70c9753ec4f22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230411"
---
# <a name="texture-class"></a>texture 類別

材質是範圍定義域中的資料匯總 `accelerator_view` 。 它是變數的集合，範圍定義域中的每個元素各一個。 每個變數都包含一個對應至 c + + 基本型別（ **`unsigned int`** 、 **`int`** 、 **`float`** 、 **`double`** ）、純量型別（ `norm` 、或 `unorm` ）或短向量型別的值。

## <a name="syntax"></a>語法

```cpp
template <typename value_type,  int _Rank>
class texture;
```

### <a name="parameters"></a>參數

*value_type*<br/>
材質中元素的類型。

*_Rank*<br/>
材質的順位。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`scalar_type`|純量類型。|
|`value_type`|實數值型別。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[材質函數](#ctor)|初始化 `texture` 類別的新執行個體。|
|[~ 材質析構函式](#ctor)|終結 `texture` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[copy_to](#copy_to)|藉 `texture` 由執行深層複製，將物件複製到目的地。|
|[data](#data)|將 CPU 指標傳回此材質的原始資料。|
|[get](#get)|傳回指定索引處的元素值。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|傳回要將此材質複製到其中的慣用目標[accelerator_view](accelerator-view-class.md) 。|
|[get_depth_pitch](#get_depth_pitch)|傳回 CPU 上3D 暫存材質中每個深度配量之間的位元組數目。|
|[get_row_pitch](#get_row_pitch)|傳回 CPU 上2D 或3D 暫存材質中每個資料列之間的位元組數目。|
|[set](#set)|設定指定索引處的元素值。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[operator （）](#operator_call)|傳回參數所指定的元素值。|
|[操作\[\]](#operator_at)|傳回位於指定索引處的元素。|
|[operator =](#operator_eq)|將指定的[材質](texture-class.md)物件複製到這個。|

### <a name="public-constants"></a>公用常數

|名稱|說明|
|----------|-----------------|
|[次序常數](#rank)|取得物件的順位 `texture` 。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|取得要複製到這個材質慣用目標的[accelerator_view](accelerator-view-class.md) 。|
|[depth_pitch](#depth_pitch)|取得 CPU 上3D 暫存材質中每個深度配量之間的位元組數目。|
|[row_pitch](#row_pitch)|取得 CPU 上2D 或3D 暫存材質中每個資料列之間的位元組數目。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Texture_base`

`texture`

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** Concurrency：： graphics

## <a name="texture"></a><a name="dtor"></a>~ 材質

終結 `texture` 物件。

```cpp
~texture() restrict(cpu);
```

## <a name="associated_accelerator_view"></a><a name="associated_accelerator_view"></a>associated_accelerator_view

取得要複製到這個材質慣用目標的[accelerator_view](accelerator-view-class.md) 。

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a><a name="copy_to"></a>copy_to

藉 `texture` 由執行深層複製，將物件複製到目的地。

```cpp
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要複製的物件。

*_Rank*<br/>
材質的順位。

*value_type*<br/>
材質中元素的類型。

## <a name="data"></a><a name="data"></a> 資料

將 CPU 指標傳回此材質的原始資料。

```cpp
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

材質原始資料的指標。

## <a name="depth_pitch"></a><a name="depth_pitch"></a>depth_pitch

取得 CPU 上3D 暫存材質中每個深度配量之間的位元組數目。

```cpp
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

## <a name="get"></a><a name="get"></a>獲取

傳回指定索引處的元素值。

```cpp
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
項目的索引。

### <a name="return-value"></a>傳回值

位於指定索引處的項目值。

## <a name="get_associated_accelerator_view"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

傳回要將此材質複製到其中的慣用目標 accelerator_view。

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

[Accelerator_view](accelerator-view-class.md) ，這是要將此材質複製到其中的慣用目標。

## <a name="get_depth_pitch"></a><a name="get_depth_pitch"></a>get_depth_pitch

傳回 CPU 上3D 暫存材質中每個深度配量之間的位元組數目。

```cpp
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

CPU 上3D 預備材質中每個深度配量之間的位元組數目。

## <a name="get_row_pitch"></a><a name="get_row_pitch"></a>get_row_pitch

傳回二維臨時材質中的每個資料列之間，或3d 暫存材質中的每個深度配量資料列之間的位元組數目。

```cpp
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

二維臨時材質中的每個資料列之間，或3d 暫存材質中的每個深度配量資料列之間的位元組數目。

## <a name="operator"></a><a name="operator_call"></a>operator （）

傳回參數所指定的元素值。

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

*_I0*<br/>
索引中最重要的元件。

*_I1*<br/>
索引的下一個最重要的元件。

*_I2*<br/>
索引中最重要的元件。

*_Rank*<br/>
索引的順位。

### <a name="return-value"></a>傳回值

參數所指定的元素值。

## <a name="operator"></a><a name="operator_at"></a>operator []

傳回位於指定索引處的元素。

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

*_I0*<br/>
索引。

### <a name="return-value"></a>傳回值

位於指定索引處的元素。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將指定的[材質](texture-class.md)物件複製到這個。

```cpp
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`texture`要複製的物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `texture` 。

## <a name="rank"></a><a name="rank"></a>等級

取得物件的順位 `texture` 。

```cpp
static const int rank = _Rank;
```

## <a name="row_pitch"></a><a name="row_pitch"></a>row_pitch

取得 CPU 上2D 或3D 暫存材質中每個資料列之間的位元組數目。

```cpp
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

## <a name="set"></a><a name="set"></a>設定

設定指定索引處的元素值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
項目的索引。

*_Rank*<br/>
索引的順位。

*value*<br/>
項目的新值。

## <a name="texture"></a><a name="ctor"></a>層

初始化 `texture` 類別的新執行個體。

```cpp
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>參數

*_Acc_view*<br/>
指定材質位置的[accelerator_view](accelerator-view-class.md) 。

*_Av*<br/>
指定材質位置的[accelerator_view](accelerator-view-class.md) 。

*_Associated_av*<br/>
Accelerator_view，指定從這個材質複製到或的慣用目標。

*_Bits_per_scalar_element*<br/>
紋理的基礎純量類型中每個純量元素的位數。 一般而言，支援的值為8、16、32和64。 如果指定0，則位數目會與基礎 scalar_type 相同。 64僅適用于以雙重為基礎的材質。

*_Ext*<br/>
材質之每個維度中的範圍。

*_E0*<br/>
材質最重要的元件。

*_E1*<br/>
材質的下一個最重要的元件。

*_E2*<br/>
紋理範圍中最重要的元件。

*_Input_iterator*<br/>
輸入迭代器的類型。

*_Mipmap_levels*<br/>
基礎材質中的 mipmap 層級數目。 如果指定0，材質會將 mipmap 層級的完整範圍縮小至指定範圍的最小可能大小。

*_Rank*<br/>
範圍的順位。

*_Source*<br/>
主機緩衝區的指標。

*_Src*<br/>
要複製的材質。

*_Src_byte_size*<br/>
來源緩衝區中的位元組數目。

*_Src_first*<br/>
來源容器中的開始反覆運算器。

*_Src_last*<br/>
來源容器中的結束反覆運算器。

*_Other*<br/>
其他資料來源。

*_Rank*<br/>
區段的順位。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

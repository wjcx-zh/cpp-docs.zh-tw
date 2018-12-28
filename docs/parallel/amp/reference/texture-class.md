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
ms.openlocfilehash: 8e427206379f1e7d094362411f074ad9cafb43fd
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657535"
---
# <a name="texture-class"></a>texture 類別

材質是將資料彙總上`accelerator_view`在範圍內。 它是變數，每個項目，對應範圍網域中的集合。 每個變數會保留對應到 c + + 基本類型的值 ( `unsigned int`， `int`， `float`， `double`)、 純量類型 ( `norm`，或`unorm`)，或短向量類型。

## <a name="syntax"></a>語法

```
template <typename value_type,  int _Rank>
class texture;
```

#### <a name="parameters"></a>參數

*value_type*<br/>
材質中項目的類型。

*_Rank*<br/>
材質的順位。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|描述|
|----------|-----------------|
|`scalar_type`|純量類型。|
|`value_type`|實值型別。|

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[材質的建構函式](#ctor)|初始化 `texture` 類別的新執行個體。|
|[~ texture 解構函式](#ctor)|終結`texture`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[copy_to](#copy_to)|複製`texture`物件到目的地，所進行的深層複本。|
|[data](#data)|傳回此材質的未經處理資料的 CPU 指標。|
|[get](#get)|傳回指定索引處的項目值。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)也就是要複製到此材質的慣用的目標。|
|[get_depth_pitch](#get_depth_pitch)|傳回的 3D 預備環境在 CPU 上的紋理中每個深度切割之間的位元組數目。|
|[get_row_pitch](#get_row_pitch)|傳回位元組的數目之間的 2D 或 3D 預備環境材質在 CPU 上的每個資料列。|
|[set](#set)|指定索引處設定項目的值。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator()](#operator_call)|傳回參數所指定的項目值。|
|[operator\[\]](#operator_at)|傳回位於指定索引處的項目。|
|[operator=](#operator_eq)|複製指定[紋理](texture-class.md)如下的物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|取得的順位`texture`物件。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|取得[accelerator_view](accelerator-view-class.md)也就是要複製到此材質的慣用的目標。|
|[depth_pitch](#depth_pitch)|取得在 CPU 上的 3D 預備環境材質中每個深度切割之間的位元組數目。|
|[row_pitch](#row_pitch)|取得 2D 或 3D 中每個資料列之間的位元組數目的臨時在 CPU 上的紋理。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_Texture_base`

`texture`

## <a name="requirements"></a>需求

**標頭：** amp_graphics.h

**命名空間：** Concurrency:: graphics

##  <a name="dtor"></a> ~ 紋理

終結`texture`物件。

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

取得[accelerator_view](accelerator-view-class.md)也就是要複製到此材質的慣用的目標。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

複製`texture`物件到目的地，所進行的深層複本。

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要複製到的物件。

*_Rank*<br/>
材質的順位。

*value_type*<br/>
材質中項目的類型。

##  <a name="data"></a> 資料

傳回此材質的未經處理資料的 CPU 指標。

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

材質的未經處理資料指標。

##  <a name="depth_pitch"></a> depth_pitch

取得在 CPU 上的 3D 預備環境材質中每個深度切割之間的位元組數目。

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> 取得

傳回指定索引處的項目值。

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
項目的索引。

### <a name="return-value"></a>傳回值

位於指定索引處的項目值。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

傳回是要複製到此材質的慣用的目標的 accelerator_view。

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

[Accelerator_view](accelerator-view-class.md)也就是要複製到此材質的慣用的目標。

##  <a name="get_depth_pitch"></a> get_depth_pitch

傳回的 3D 預備環境在 CPU 上的紋理中每個深度切割之間的位元組數目。

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

中的 3D 預備環境材質在 CPU 上的每個深度切割之間的位元組數目。

##  <a name="get_row_pitch"></a> get_row_pitch

2d 預備環境材質中，每個資料列或 3d 預備環境材質中深度切割每一列之間，則傳回位元組的數目。

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

2d 預備環境材質中，每個資料列或 3d 預備環境材質中深度切割每一列之間的位元組數目。

##  <a name="operator_call"></a> operator （)

傳回參數所指定的項目值。

```
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
索引的重要元件。

*_I1*<br/>
索引的下一步 以-重要的元件。

*_I2*<br/>
索引的最小顯著性的元件。

*_Rank*<br/>
索引的順位。

### <a name="return-value"></a>傳回值

參數所指定項目值。

##  <a name="operator_at"></a> operator]

傳回位於指定索引處的項目。

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

*_I0*<br/>
索引。

### <a name="return-value"></a>傳回值

位於指定索引處的項目。

##  <a name="operator_eq"></a> 運算子 =

複製指定[紋理](texture-class.md)如下的物件。

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`texture`從複製的物件。

### <a name="return-value"></a>傳回值

此參考`texture`物件。

##  <a name="rank"></a> 陣序規範

取得的順位`texture`物件。

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

取得 2D 或 3D 中每個資料列之間的位元組數目的臨時在 CPU 上的紋理。

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> 設定

指定索引處設定項目的值。

```
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

##  <a name="ctor"></a> 材質

初始化 `texture` 類別的新執行個體。

```
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
[Accelerator_view](accelerator-view-class.md)指定材質的位置。

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md)指定材質的位置。

*_Associated_av*<br/>
指定複本，或從此材質的慣用的目標 accelerator_view。

*_Bits_per_scalar_element*<br/>
每個基礎純量類型的紋理中每個純量元素的位元數。 一般情況下，支援的值為 8、 16、 32 和 64。 如果指定 0 時，位元數是與基礎 scalar_type 相同。 64 僅適用於 double 材質。

*_Ext*<br/>
在每個維度中紋理的範圍。

*_E0*<br/>
材質的最重要的元件。

*_E1*<br/>
材質的下一步 以-重要的元件。

*_E2*<br/>
材質範圍的最不重要元件。

*_Input_iterator*<br/>
輸入迭代器類型。

*_Mipmap_levels*<br/>
基礎材質中 mipmap 層級數目。 如果指定 0，材質會有完整的 mipmap 層級指定範圍的最小大小。

*_Rank*<br/>
範圍的順位。

*_Source*<br/>
主機緩衝區的指標。

*_Src*<br/>
若要複製的材質。

*_Src_byte_size*<br/>
來源緩衝區中的位元組數目。

*_Src_first*<br/>
來源容器中的開頭迭代器。

*_Src_last*<br/>
來源容器中結束迭代器。

*_Other*<br/>
其他資料來源。

*_Rank*<br/>
區段的順位。

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

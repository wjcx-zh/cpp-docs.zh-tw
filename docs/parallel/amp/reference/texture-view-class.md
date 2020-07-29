---
title: texture_view 類別
ms.date: 11/04/2016
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 1fa21f2a5a5c1d004fc23d70b686d7e45bbcac81
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215903"
---
# <a name="texture_view-class"></a>texture_view 類別

提供材質的讀取存取和寫入權限。 `texture_view`只能用來讀取其數值型別為 **`int`** 、 **`unsigned int`** 或 **`float`** 且具有預設32位 bpse 的材質。 若要讀取其他材質格式，請使用 `texture_view<const value_type, _Rank>` 。

## <a name="syntax"></a>語法

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>參數

*value_type*<br/>
材質匯總中元素的類型。

*_Rank*<br/>
的排名 `texture_view` 。

## <a name="members"></a>成員

### <a name="public-typedefs"></a>公用 Typedefs

|名稱|說明|
|----------|-----------------|
|`value_type`|材質匯總中元素的類型。|
|`coordinates_type`|用來在中指定材質的座標類型， `texture_view` 也就是，其次序與 `short_vector` 具有之數值型別的關聯材質相同 **`float`** 。|
|`gather_return_type`|用於收集作業的傳回型別，也就是會 `short_vector` 保存四個同質色彩元件，並從取樣的四個材質值收集而來的次序4。|

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[texture_view 的構造函式](#ctor)|已多載。 結構 `texture_view` 實例。|
|[~ texture_view 的析構函式](#ctor)|損毀 `texture_view` 實例。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[gather_Alpha](#gather_alpha)|已多載。 使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的 Alpha （w）元件。|
|[gather_blue](#gather_blue)|已多載。 使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的藍色（z）元件。|
|[gather_green](#gather_green)|已多載。 使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的綠色（y）元件。|
|[gather_red](#gather_red)|已多載。 使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的紅色（x）元件。|
|[get](#get)|已多載。 依索引取得元素值。|
|[抽樣](#sample)|已多載。 使用指定的取樣設定，以指定的座標和詳細資料層級來取樣材質。|
|[set](#set)|依索引設定元素的值。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[operator （）](#operator_call)|已多載。 依索引取得元素值。|
|[操作\[\]](#operator_at)|已多載。 依索引取得元素值。|
|[operator =](#operator_eq)|已多載。 指派運算子。|

### <a name="public-data-members"></a>公用資料成員

|名稱|說明|
|----------|-----------------|
|[value_type](#value_type)|元素的實值型別 `texture_view` 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`_Texture_base`

`texture_view`

## <a name="requirements"></a>需求

**標頭：** amp_graphics。h

**命名空間：** concurrency：： graphics

## <a name="texture_view"></a><a name="dtor"></a>~ texture_view

損毀 `texture_view` 實例。

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="texture_view"></a><a name="ctor"></a>texture_view

結構 `texture_view` 實例。

```cpp
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>參數

*_Src*<br/>
[1，2]`texture`建立可寫入之的的「構造函式」 `texture_view` 。

[3，4]在 `texture` 其上建立不可寫入的的「構造函式」 `texture_view` 。

*_Other*<br/>
[5] 複製可寫入來源的函式 `texture_view` 。

[6，7]複製不能寫入的來源 `texture_view` 。

*_Mipmap_level*<br/>
來源上可寫入之系結的特定 mipmap 層級 `texture` `texture_view` 。 預設值為0，代表最上層（最詳細的） mip 層級。

*_Most_detailed_mip*<br/>
視圖的最上層（最詳細） mip 層級，相對於指定的 `texture_view` 物件。

*_Mip_levels*<br/>
可透過存取的 mipmap 層級數目 `texture_view` 。

## <a name="gather_red"></a><a name="gather_red"></a>gather_red

使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的紅色（x）元件。

```cpp
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Address_mode*<br/>
要用來取樣的位址模式 `texture_view` 。 所有維度的位址模式都相同。

*_Sampler*<br/>
要用來取樣的取樣器設定 `texture_view` 。

*_Coord*<br/>
要從中執行樣本的座標。 小數座標值是用來在範例材質之間插入。

### <a name="return-value"></a>傳回值

排名4的短向量，其中包含4個取樣材質值的紅色（x）元件。

## <a name="gather_green"></a><a name="gather_green"></a>gather_green

使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的綠色（y）元件。

```cpp
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Address_mode*<br/>
要用來取樣的位址模式 `texture_view` 。 所有維度的位址模式都相同。

*_Sampler*<br/>
要用來取樣的取樣器設定 `texture_view` 。

*_Coord*<br/>
要從中執行樣本的座標。 小數座標值是用來在範例材質之間插入。

### <a name="return-value"></a>傳回值

排名4的短向量，其中包含4個取樣材質值的綠色（y）元件。

## <a name="gather_blue"></a><a name="gather_blue"></a>gather_blue

使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的藍色（z）元件。

```cpp
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Address_mode*<br/>
要用來取樣的位址模式 `texture_view` 。 所有維度的位址模式都相同。

*_Sampler*<br/>
要用來取樣的取樣器設定 `texture_view` 。

*_Coord*<br/>
要從中執行樣本的座標。 小數座標值是用來在範例材質之間插入。

### <a name="return-value"></a>傳回值

排名4的短向量，其中包含4個取樣材質值的紅色（x）元件。

## <a name="gather_alpha"></a><a name="gather_alpha"></a>gather_Alpha

使用指定的取樣設定，在指定的座標上取樣材質，並傳回四個取樣材質的 Alpha （w）元件。

```cpp
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Address_mode*<br/>
要用來取樣的位址模式 `texture_view` 。 所有維度的位址模式都相同。

*_Sampler*<br/>
要用來取樣的取樣器設定 `texture_view` 。

*_Coord*<br/>
要從中執行樣本的座標。 小數座標值是用來在範例材質之間插入。

### <a name="return-value"></a>傳回值

排名4的短向量，其中包含4個取樣材質值的 Alpha （w）元件。

## <a name="get"></a><a name="get"></a>獲取

取得位於指定索引處之專案的值。

```cpp
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
要取得的專案索引，可能是多維度的。

*_Mip_level*<br/>
我們應該從中取得值的 mipmap 層級。 預設值0代表最詳細的 mipmap 層級。

### <a name="return-value"></a>傳回值

元素的值。

## <a name="operator"></a><a name="operator_eq"></a>operator =

將與指定之相同材質的視圖指派 `texture_view` 給這個 `texture_view` 實例。

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
[1，2]複製構造函式可寫入的 `texture_view` 物件。

[3] 複製不是可寫入物件的構造函式 `texture_view` 。

### <a name="return-value"></a>傳回值

這個實例的參考 `texture_view` 。

## <a name="operator"></a><a name="operator_at"></a>operator []

依索引傳回元素值。

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引，可能是多維度。

*_I0*<br/>
一維索引。

### <a name="return-value"></a>傳回值

以編制索引的元素值 `_Index` 。

## <a name="operator"></a><a name="operator_call"></a>operator （）

依索引傳回元素值。

```cpp
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引，可能是多維度。

*_I0*<br/>
索引中最重要的元件。

*_I1*<br/>
索引的下一個最重要的元件。

*_I2*<br/>
索引中最重要的元件。

### <a name="return-value"></a>傳回值

以編制索引的元素值 `_Index` 。

## <a name="sample"></a><a name="sample"></a>抽樣

使用指定的取樣設定，以指定的座標和詳細資料層級來取樣材質。

```cpp
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Filter_mode*<br/>
用來取樣 texture_view 的篩選模式。 [最小化]、[極大化] 和 [mipmap] 篩選準則的篩選模式都相同。

*_Address_mode*<br/>
用來取樣 texture_view 的位址模式。 所有維度的位址模式都相同。

*_Sampler*<br/>
要用來取樣 texture_view 的取樣器設定。

*_Coord*<br/>
要從中執行樣本的座標。 小數座標值是用來在材質值之間插補。

*_Level_of_detail*<br/>
值會指定要做為取樣來源的 mipmap 層級。 小數值是用來在兩個 mipmap 層級之間插補。 預設的詳細資料層級為0，表示最詳細的 mip 層級。

### <a name="return-value"></a>傳回值

插補範例值。

## <a name="set"></a><a name="set"></a>設定

將指定索引處的元素值設定為指定的值。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>參數

*_Index*<br/>
要設定之專案的索引，可能是多維度的。

*value*<br/>
要設定元素的值。

## <a name="value_type"></a><a name="value_type"></a>value_type

Texture_view 元素的實值型別。

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>另請參閱

[Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

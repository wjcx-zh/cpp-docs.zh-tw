---
title: texture_view 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3db02d9cafb87c0f173546687ad01390e09b9f68
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696262"
---
# <a name="textureview-class"></a>texture_view 類別
提供對紋理的寫入權限和讀取權限。 `texture_view` 只可以用來讀取其值類型的紋理`int`， `unsigned int`，或`float`具有預設值 32 位元 bpse。 若要閱讀其他紋理的格式，使用`texture_view<const value_type, _Rank>`。  
  
## <a name="syntax"></a>語法  
  
```  
template<typename value_type,int _Rank>  
class texture_view;  
 
template<typename value_type, int _Rank>  
class texture_view 
   : public details::_Texture_base<value_type, _Rank>;  
 
template<typename value_type, int _Rank>  
class texture_view<const value_type, _Rank> 
   : public details::_Texture_base<value_type, _Rank>;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 紋理彙總中的項目類型。  
  
 `_Rank`  
 陣序`texture_view`。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`value_type`|紋理彙總中的項目類型。|  
|`coordinates_type`|用來指定在材質座標的型別`texture_view`— 也就是`short_vector`具有相關聯的紋理，其的實值類型為相同的陣序`float`。|  
|`gather_return_type`|傳回型別用於收集作業 — 也就是次序 4`short_vector`保存的四個同質性色彩元件收集取樣的四個材質值。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[texture_view 建構函式](#ctor)|多載。 建構`texture_view`執行個體。|  
|[~ texture_view 解構函式](#ctor)|終結`texture_view`執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|多載。 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的 alpha (w) 元件。|  
|[gather_blue](#gather_blue)|多載。 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的藍色 (z) 元件。|  
|[gather_green](#gather_green)|多載。 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的綠色 (y) 元件。|  
|[gather_red](#gather_red)|多載。 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的紅色 (x) 元件。|  
|[get](#get)|多載。 依索引取得的項目值。|  
|[範例](#sample)|多載。 使用指定的取樣設定取樣的紋理指定的座標和層級的詳細資料。|  
|[set](#set)|依索引設定項目的值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator()](#operator_call)|多載。 依索引取得的項目值。|  
|[operator[]](#operator_at)|多載。 依索引取得的項目值。|  
|[operator=](#operator_eq)|多載。 指派運算子。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[value_type](#value_type)|實值型別項目的`texture_view`。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Texture_base`  
  
 `texture_view`  
  
## <a name="requirements"></a>需求  
 **標頭：** amp_graphics.h  
  
 **命名空間：** concurrency:: graphics  
  
##  <a name="dtor"></a> ~ texture_view 

 終結`texture_view`執行個體。  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="ctor"></a> texture_view 

 建構`texture_view`執行個體。  
  
```  
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
 `_Src`  
 [1，2]建構函式  
 `texture`所在的可寫入`texture_view`建立。  
  
 [3，4]建構函式  
 `texture`上不能寫入`texture_view`建立。  
  
 `_Other`  
 [5] 複製建構函式  
 可寫入的來源`texture_view`。  
  
 [6，7]複製建構函式  
 無法寫入來源`texture_view`。  
  
 `_Mipmap_level`  
 在來源上特定的 mipmap 層次`texture`這個可寫入`texture_view`繫結。 預設值是 0，代表最上層 （最不詳細） mip 層級。  
  
 `_Most_detailed_mip`  
 排名最前面 （最不詳細） 層級檢視中，相對於指定的 mip 層級`texture_view`物件。  
  
 `_Mip_levels`  
 可透過存取 mipmap 層次數目`texture_view`。  
  
##  <a name="gather_red"></a> gather_red 

 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的紅色 (x) 元件。  
  
```  
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
 `_Address_mode`  
 若要使用的位址模式範例`texture_view`。 位址模式也適用於所有的維度。  
  
 `_Sampler`  
 要使用的取樣器組態範例`texture_view`。  
  
 `_Coord`  
 要採取的範例的座標。 小數的座標值用於範例材質間進行插補。  
  
### <a name="return-value"></a>傳回值  
 包含 4 的紅色 (x) 元件的陣序規範 4 短向量取樣材質值。  
  
##  <a name="gather_green"></a> gather_green 

 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的綠色 (y) 元件。  
  
```  
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
 `_Address_mode`  
 若要使用的位址模式範例`texture_view`。 位址模式也適用於所有的維度。  
  
 `_Sampler`  
 要使用的取樣器組態範例`texture_view`。  
  
 `_Coord`  
 要採取的範例的座標。 小數的座標值用於範例材質間進行插補。  
  
### <a name="return-value"></a>傳回值  
 包含 4 的綠色 (y) 元件的陣序規範 4 短向量取樣材質值。  
  
##  <a name="gather_blue"></a> gather_blue 

 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的藍色 (z) 元件。  
  
```  
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
 `_Address_mode`  
 若要使用的位址模式範例`texture_view`。 位址模式也適用於所有的維度。  
  
 `_Sampler`  
 要使用的取樣器組態範例`texture_view`。  
  
 `_Coord`  
 要採取的範例的座標。 小數的座標值用於範例材質間進行插補。  
  
### <a name="return-value"></a>傳回值  
 包含 4 的紅色 (x) 元件的陣序規範 4 短向量取樣材質值。  
  
##  <a name="gather_alpha"></a> gather_alpha 

 使用指定的取樣的組態範例指定座標上的紋理，並傳回四個取樣材質的 alpha (w) 元件。  
  
```  
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
 `_Address_mode`  
 若要使用的位址模式範例`texture_view`。 位址模式也適用於所有的維度。  
  
 `_Sampler`  
 要使用的取樣器組態範例`texture_view`。  
  
 `_Coord`  
 要採取的範例的座標。 小數的座標值用於範例材質間進行插補。  
  
### <a name="return-value"></a>傳回值  
 陣序規範 4 短向量包含 alpha (w) 元件的 4 取樣材質值。  
  
##  <a name="get"></a> 取得 

 取得指定索引處的元素的值。  
  
```  
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

 
value_type get(
    const index<_Rank>& _Index,  
    unsigned int _Mip_level = 0) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 若要取得，可能是多維度的項目索引。  
  
 `_Mip_level`  
 Mipmap 層次，我們應該從中取得的值。 預設值 0 表示最詳細的 mipmap 層次。  
  
### <a name="return-value"></a>傳回值  
 項目的值。  
  
##  <a name="operator_eq"></a> 運算子 = 

 指派與指定的相同紋理檢視`texture_view`至此`texture_view`執行個體。  
  
```  
texture_view<value_type, _Rank>& operator= (// [1] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

 
texture_view<const value_type, _Rank>& operator= (// [2] copy constructor  
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

 
texture_view<const value_type, _Rank>& operator= (// [3] copy constructor  
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 [1，2]複製建構函式  
 可寫入`texture_view`物件。  
  
 [3] 複製建構函式  
 不能寫入`texture_view`物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`texture_view`執行個體。  
  
##  <a name="operator_at"></a> operator] 

 依索引傳回項目值。  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);

 
value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 索引中，可能是多維度。  
  
 `_I0`  
 一維索引。  
  
### <a name="return-value"></a>傳回值  
 以編製索引的項目值`_Index`。  
  
##  <a name="operator_call"></a> operator （) 

 依索引傳回項目值。  
  
```  
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
 `_Index`  
 索引中，可能是多維度。  
  
 `_I0`  
 索引的最有效的元件。  
  
 `_I1`  
 索引的下一步-到-最高有效的元件。  
  
 `_I2`  
 索引的最小顯著性的元件。  
  
### <a name="return-value"></a>傳回值  
 以編製索引的項目值`_Index`。  
  
##  <a name="sample"></a> 範例 

 使用指定的取樣設定取樣的紋理指定的座標和層級的詳細資料。  
  
```  
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
 `_Filter_mode`  
 使用取樣 texture_view 的篩選模式。 篩選模式也適用於最小化、 最大化和 mipmap 篩選器。  
  
 `_Address_mode`  
 使用取樣 texture_view 位址模式。 位址模式也適用於所有的維度。  
  
 `_Sampler`  
 要使用取樣 texture_view 的取樣器組態。  
  
 `_Coord`  
 要採取的範例的座標。 小數的座標值可用來材質值之間進行插補。  
  
 `_Level_of_detail`  
 此值會指定要取樣的 mipmap 層次。 小數的值可用來插入兩個 mipmap 層次。 詳細資料的預設層級是 0，代表最詳細的 mip 層級。  
  
### <a name="return-value"></a>傳回值  
 插補的範例值。  
  
##  <a name="set"></a> 設定 

 將項目的值設定為指定的值的指定索引處。  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 若要設定，可能是多維度的項目索引。  
  
 `value`  
 若要設定項目的值。  
  
##  <a name="value_type"></a> value_type 

 Texture_view 元素的值型別。  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

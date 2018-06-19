---
title: texture 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b16e449f3def7b4b86932e9806fa78d422466978
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692778"
---
# <a name="texture-class"></a>texture 類別
紋理是將資料彙總上`accelerator_view`範圍網域中。 它是變數，其中每個項目範圍網域中的集合。 每個變數會保存至 c + + 基本類型對應的值 ( `unsigned int`， `int`， `float`， `double`)、 純量類型 ( `norm`，或`unorm`)，或短向量類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename value_type,  int _Rank>  
class texture;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 紋理中的項目類型。  
  
 `_Rank`  
 紋理的陣序規範。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`scalar_type`|純量類型。|  
|`value_type`|實值類型。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[紋理建構函式](#ctor)|初始化 `texture` 類別的新執行個體。|  
|[~ texture 解構函式](#ctor)|終結`texture`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[copy_to](#copy_to)|複製`texture`物件到目的地時，所進行的深層複本。|  
|[data](#data)|傳回這個的紋理的未經處理資料的 CPU 指標。|  
|[get](#get)|傳回指定索引處的項目值。|  
|[get_associated_accelerator_view](#get_associated_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)也就是要複製到這個紋理的慣用的目標。|  
|[get_depth_pitch](#get_depth_pitch)|傳回位元組的數目之間 3D 暫存 CPU 上的紋理中的每個深度切割。|  
|[get_row_pitch](#get_row_pitch)|傳回位元組的數目之間 2D 或 3D 暫存 CPU 上的紋理中的每個資料列。|  
|[set](#set)|設定指定索引處的元素的值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator()](#operator_call)|傳回參數所指定的項目值。|  
|[operator[]](#operator_at)|傳回指定索引處的項目。|  
|[operator=](#operator_eq)|複製指定[紋理](texture-class.md)給這一個物件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[rank 常數](#rank)|取得的順位`texture`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[associated_accelerator_view](#associated_accelerator_view)|取得[accelerator_view](accelerator-view-class.md)也就是要複製到這個紋理的慣用的目標。|  
|[depth_pitch](#depth_pitch)|取得在 CPU 上臨時 3D 材質中每個深度切割之間的位元組數目。|  
|[row_pitch](#row_pitch)|取得以 2D 或 3D 每個資料列之間的位元組數的暫存 CPU 上的紋理。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>需求  
 **標頭：** amp_graphics.h  
  
 **命名空間：** concurrency:: graphics  
  
##  <a name="dtor"></a> ~ 紋理 

 終結`texture`物件。  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="associated_accelerator_view"></a> associated_accelerator_view 

 取得[accelerator_view](accelerator-view-class.md)也就是要複製到這個紋理的慣用的目標。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="copy_to"></a> copy_to 

 複製`texture`物件到目的地時，所進行的深層複本。  
  
```  
void copy_to(texture& _Dest) const; 
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const; 
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要複製到的物件。  
  
 `_Rank`  
 紋理的陣序規範。  
  
 `value_type`  
 紋理中的項目類型。  
  
##  <a name="data"></a> 資料 

 傳回這個的紋理的未經處理資料的 CPU 指標。  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 紋理的未經處理資料指標。  
  
##  <a name="depth_pitch"></a> depth_pitch 

 取得在 CPU 上臨時 3D 材質中每個深度切割之間的位元組數目。  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="get"></a> 取得 

 傳回指定索引處的項目值。  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 項目的索引。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的項目值。  
  
##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view 

 傳回這個紋理複製到其中的慣用目標 accelerator_view。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 [Accelerator_view](accelerator-view-class.md)也就是要複製到這個紋理的慣用的目標。  
  
##  <a name="get_depth_pitch"></a> get_depth_pitch 

 傳回位元組的數目之間 3D 暫存 CPU 上的紋理中的每個深度切割。  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 3D 暫存 CPU 上的紋理中的每個深度切割之間的位元組數目。  
  
##  <a name="get_row_pitch"></a> get_row_pitch 

 深度配量 3d 臨時的紋理中的每個資料列或 2 維度的臨時材質中每個資料列之間，則傳回位元組的數目。  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 深度配量 3d 臨時的紋理中的每個資料列或 2 維度的臨時材質中每個資料列之間的位元組數目。  
  
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
 `_Index`  
 索引。  
  
 `_I0`  
 索引的最有效的元件。  
  
 `_I1`  
 索引的下一步-到-最高有效的元件。  
  
 `_I2`  
 索引的最小顯著性的元件。  
  
 `_Rank`  
 索引的陣序規範。  
  
### <a name="return-value"></a>傳回值  
 參數所指定項目值。  
  
##  <a name="operator_at"></a> operator] 

 傳回指定索引處的項目。  
  
```  
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

 
const value_type operator[] (int _I0) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 索引。  
  
 `_I0`  
 索引。  
  
### <a name="return-value"></a>傳回值  
 所指定索引處的項目。  
  
##  <a name="operator_eq"></a> 運算子 = 

 複製指定[紋理](texture-class.md)給這一個物件。  
  
```  
texture& operator= (
    const texture& _Other);

 
texture& operator= (
    texture<value_type, _Rank>&& _Other);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `texture`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`texture`物件。  
  
##  <a name="rank"></a> 順位 

 取得的順位`texture`物件。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="row_pitch"></a> row_pitch 

 取得以 2D 或 3D 每個資料列之間的位元組數的暫存 CPU 上的紋理。  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="set"></a> 設定 

 設定指定索引處的元素的值。  
  
```  
void set(
    const index<_Rank>& _Index,  
    const value_type& value) restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 項目的索引。  
  
 `_Rank`  
 索引的陣序規範。  
  
 `value`  
 項目的新值。  
  
##  <a name="ctor"></a> 紋理 

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
 `_Acc_view`  
 [Accelerator_view](accelerator-view-class.md)指定紋理的位置。  
  
 `_Av`  
 [Accelerator_view](accelerator-view-class.md)指定紋理的位置。  
  
 `_Associated_av`  
 指定的慣用的目標 accelerator_view 複製到資料表或從這個的紋理。  
  
 `_Bits_per_scalar_element`  
 每個基礎紋理的純量型別中每個純量元素的位元數。 一般情況下，支援的值是 8、 16、 32 和 64。 如果指定 0 時，位元數是基礎 scalar_type 相同。 只有適用於雙基礎紋理 64。  
  
 `_Ext`  
 紋理的每個維度中的延伸區。  
  
 `_E0`  
 紋理的最重要的元件。  
  
 `_E1`  
 紋理的下一步-到-最高有效的元件。  
  
 `_E2`  
 紋理的範圍的最不重要的元件。  
  
 `_Input_iterator`  
 輸入 interator 類型。  
  
 `_Mipmap_levels`  
 在基礎紋理的 mipmap 層次數目。 如果指定 0 時，紋理必須向最可能的最小大小，為指定範圍的 mipmap 層次的完整範圍。  
  
 `_Rank`  
 範圍陣序。  
  
 `_Source`  
 主機緩衝區的指標。  
  
 `_Src`  
 若要複製的材質。  
  
 `_Src_byte_size`  
 來源緩衝區的位元組數目。  
  
 `_Src_first`  
 插入來源容器開頭迭代器。  
  
 `_Src_last`  
 插入來源容器結尾迭代器。  
  
 `_Other`  
 其他資料來源。  
  
 `_Rank`  
 區段的陣序規範。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency::graphics 命名空間](concurrency-graphics-namespace.md)

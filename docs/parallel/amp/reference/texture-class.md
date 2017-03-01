---
title: "紋理類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::texture
dev_langs:
- C++
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: aafb23ac4d366baed37f1cf667984253160af9c3
ms.lasthandoff: 02/24/2017

---
# <a name="texture-class"></a>texture 類別
紋理是將資料彙總上`accelerator_view`範圍網域中。 它是每個項目範圍網域中的變數集合。 每個變數會保留對應至 c + + 基本類型的值 ( `unsigned int`， `int`， `float`， `double`)，純量型別 ( `norm`，或`unorm`)，或短向量類型。  
  
## <a name="syntax"></a>語法  
  
```  
template <
    typename value_type,  
    int _Rank  
>  
class texture;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 紋理中的項目類型。  
  
 `_Rank`  
 紋理的陣序規範。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`scalar_type`|純量型別。|  
|`value_type`|實值型別。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[紋理建構函式](#ctor)|初始化 `texture` 類別的新執行個體。|  
|[~ texture 解構函式](#ctor)|終結`texture`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[copy_to 方法](#copy_to)|複製`texture`物件到目的地時，所進行的深層複本。|  
|[資料方法](#data)|傳回這個紋理的未經處理資料的 CPU 指標。|  
|[get 方法](#get)|傳回指定索引處的項目值。|  
|[get_associated_accelerator_view 方法](#get_associated_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)也就是複製到這個紋理的慣用的目標。|  
|[get_depth_pitch 方法](#get_depth_pitch)|傳回位元組的數目之間預備 CPU 上的紋理 3D 模式中的每個深度配量。|  
|[get_row_pitch 方法](#get_row_pitch)|傳回位元組的數目之間 2D 或 3D 預備 CPU 上的紋理中的每個資料列。|  
|[set 方法](#set)|指定索引處設定項目的值。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator （) 運算子](#operator_call)|傳回參數所指定的項目值。|  
|[operator [] 運算子](#operator_at)|傳回指定索引處的項目。|  
|[運算子 = 運算子](#operator_eq)|複製指定[紋理](texture-class.md)這個物件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[rank 常數](#rank)|取得的順位`texture`物件。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[associated_accelerator_view 資料成員](#associated_accelerator_view)|取得[accelerator_view](accelerator-view-class.md)也就是複製到這個紋理的慣用的目標。|  
|[depth_pitch 資料成員](#depth_pitch)|取得在 CPU 上的 3D 臨時紋理的每個深度配量之間的位元組數目。|  
|[row_pitch 資料成員](#row_pitch)|取得 2D 或 3D 每個資料列之間的位元組數目的臨時 CPU 上的紋理。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Texture_base`  
  
 `texture`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp_graphics.h  
  
 **命名空間︰** concurrency:: graphics  
  
##  <a name="a-namedtora-texture"></a><a name="dtor"></a>~ 紋理 

 終結`texture`物件。  
  
```  
~texture() restrict(cpu);
```  
  
##  <a name="a-nameassociatedacceleratorviewa-associatedacceleratorview"></a><a name="associated_accelerator_view"></a>associated_accelerator_view 

 取得[accelerator_view](accelerator-view-class.md)也就是複製到這個紋理的慣用的目標。  
  
```  
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;  
```  
  
##  <a name="a-namecopytoa-copyto"></a><a name="copy_to"></a>copy_to 

 複製`texture`物件到目的地時，所進行的深層複本。  
  
```  
void copy_to(
    texture& _Dest) const;

 
 
void copy_to(
    writeonly_texture_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要複製到的物件。  
  
 `_Rank`  
 紋理的陣序規範。  
  
 `value_type`  
 紋理中的項目類型。  
  
##  <a name="a-namedataa-data"></a><a name="data"></a>資料 

 傳回這個紋理的未經處理資料的 CPU 指標。  
  
```  
void* data() restrict(cpu);

 
const void* data() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 紋理的未經處理資料指標。  
  
##  <a name="a-namedepthpitcha-depthpitch"></a><a name="depth_pitch"></a>depth_pitch 

 取得在 CPU 上的 3D 臨時紋理的每個深度配量之間的位元組數目。  
  
```  
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;  
```  
  
##  <a name="a-namegeta-get"></a><a name="get"></a>取得 

 傳回指定索引處的項目值。  
  
```  
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 項目的索引。  
  
### <a name="return-value"></a>傳回值  
 位於指定索引處的項目值。  
  
##  <a name="a-namegetassociatedacceleratorviewa-getassociatedacceleratorview"></a><a name="get_associated_accelerator_view"></a>get_associated_accelerator_view 

 傳回已複製到這個紋理的慣用的目標 accelerator_view。  
  
```  
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 [Accelerator_view](accelerator-view-class.md)也就是複製到這個紋理的慣用的目標。  
  
##  <a name="a-namegetdepthpitcha-getdepthpitch"></a><a name="get_depth_pitch"></a>get_depth_pitch 

 傳回位元組的數目之間預備 CPU 上的紋理 3D 模式中的每個深度配量。  
  
```  
unsigned int get_depth_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 預備 CPU 上的紋理 3D 模式中的每個深度配量之間的位元組數目。  
  
##  <a name="a-namegetrowpitcha-getrowpitch"></a><a name="get_row_pitch"></a>get_row_pitch 

 傳回位元組的數目，或深度配量 3d 臨時的紋理中的每個資料列之間的 2 維度的臨時紋理，每個資料列。  
  
```  
unsigned int get_row_pitch() const restrict(cpu);
```  
  
### <a name="return-value"></a>傳回值  
 在 3d 臨時紋理深度配量的每個資料列或 2 維度臨時材質中每個資料列之間的位元組數目。  
  
##  <a name="a-nameoperatorcalla-operator"></a><a name="operator_call"></a>operator （) 

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
 索引的下一步-至-最大顯著性的元件。  
  
 `_I2`  
 索引的最小顯著性的元件。  
  
 `_Rank`  
 索引的陣序規範。  
  
### <a name="return-value"></a>傳回值  
 參數所指定的項目值。  
  
##  <a name="a-nameoperatorata-operator"></a><a name="operator_at"></a>operator] 

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
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

 複製指定[紋理](texture-class.md)這個物件。  
  
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
 參考`texture`物件。  
  
##  <a name="a-nameranka-rank"></a><a name="rank"></a>陣序規範 

 取得的順位`texture`物件。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namerowpitcha-rowpitch"></a><a name="row_pitch"></a>row_pitch 

 取得 2D 或 3D 每個資料列之間的位元組數目的臨時 CPU 上的紋理。  
  
```  
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;  
```  
  
##  <a name="a-nameseta-set"></a><a name="set"></a>設定 

 指定索引處設定項目的值。  
  
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
  
##  <a name="a-namectora-texture"></a><a name="ctor"></a>紋理 

 初始化 `texture` 類別的新執行個體。  
  
```  
texture(
    const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

 
texture(
    int _E0) restrict(cpu);

 
texture(
    int _E0,  
    int _E1) restrict(cpu);

 
texture(
    int _E0,  
    int _E1,  
    int _E2) restrict(cpu);

 
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

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    const Concurrency::extent<_Rank>& _Ext, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1, _Input_iterator _Src_first, _Input_iterator _Src_last,  
    const Concurrency::accelerator_view& _Av) restrict(cpu);

 
template<
    typename _Input_iterator  
>  
texture(
    int _E0,  
    int _E1,  
    int _E2, _Input_iterator _Src_first, _Input_iterator _Src_last,  
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
 Accelerator_view 指定慣用的目標或此紋理複製。  
  
 `_Bits_per_scalar_element`  
 每個基礎紋理的純量型別中每個純量元素的位元數。 一般情況下，支援的值是 8、 16、 32 和 64。 如果指定 0，則位元數是基礎 scalar_type 相同。 僅適用於雙基礎紋理&64;。  
  
 `_Ext`  
 紋理的每個維度中的延伸區。  
  
 `_E0`  
 紋理的最重要的元件。  
  
 `_E1`  
 紋理的下一步-至-最大顯著性的元件。  
  
 `_E2`  
 紋理的範圍的最小顯著性的元件。  
  
 `_Input_iterator`  
 輸入 interator 型別。  
  
 `_Mipmap_levels`  
 在基礎紋理的 mipmap 層次數目。 如果指定 0 時，紋理會有的完整範圍的 mipmap 層次下為指定的範圍最小可能的大小。  
  
 `_Rank`  
 範圍的陣序規範。  
  
 `_Source`  
 主機緩衝區的指標。  
  
 `_Src`  
 若要複製的材質。  
  
 `_Src_byte_size`  
 來源緩衝區的位元組數目。  
  
 `_Src_first`  
 在來源容器的開頭迭代器。  
  
 `_Src_last`  
 結束迭代器，為來源容器。  
  
 `_Other`  
 其他資料來源。  
  
 `_Rank`  
 區段的陣序規範。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency:: graphics 命名空間](concurrency-graphics-namespace.md)


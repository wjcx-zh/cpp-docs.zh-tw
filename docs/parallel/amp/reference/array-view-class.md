---
title: "array_view 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
dev_langs:
- C++
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
caps.latest.revision: 21
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: e921ae841aa1eade25fdf2ec272039cc41007a9e
ms.lasthandoff: 03/31/2017

---
# <a name="arrayview-class"></a>array_view 類別
代表 N 維檢視儲存在另一個容器中的資料。  
  
## <a name="syntax"></a>語法  
  
```  
template <
    typename value_type,  
    int _Rank = 1  
>  
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
 
template <
    typename value_type,  
    int _Rank  
>  
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;  
```  
  
#### <a name="parameters"></a>參數  
 `value_type`  
 資料類型中的項目`array_view`物件。  
  
 `_Rank`  
 陣序`array_view`物件。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[array_view 建構函式](#ctor)|初始化 `array_view` 類別的新執行個體。 沒有任何預設建構函式`array<T,N>`。 所有建構函式會限制為只有在 CPU 上執行，而且無法 Direct3D 目標上執行。|  
|[~ array_view 解構函式](#ctor)|終結`array_view`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[copy_to](#copy_to)|複製的內容`array_view`要藉由呼叫指定的目的地物件`copy(*this, dest)`。|  
|[data](#data)|讓指標回到的未經處理資料`array_view`。|  
|[discard_data](#discard_data)|捨棄目前的資料，此檢視的基礎。|  
|[get_extent](#get_extent)|傳回 array_view 物件的範圍物件。|  
|[get_ref](#get_ref)|傳回索引項目的參考。|  
|[get_source_accelerator_view](#get_source_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)其中的資料來源的`array_view`所在。|  
|[重新整理](#refresh)|通知`array_view`其繫結的記憶體外部修改過的物件`array_view`介面。 呼叫這個方法會轉譯過時所有快取的資訊。|  
|[reinterpret_as](#reinterpret_as)|傳回一維陣列，包含中的所有項目`array_view`物件。|  
|[section](#section)|傳回的子區段`array_view`物件位於指定的來源，並選擇性地，具有指定的範圍。|  
|[synchronize](#synchronize)|同步處理所做的任何修改`array_view`回到其來源資料的物件。|  
|[synchronize_async](#synchronize_async)|以非同步方式同步處理所做的任何修改`array_view`回到其來源資料的物件。|  
|[synchronize_to](#synchronize_to)|同步處理所做的任何修改`array_view`到指定的物件[accelerator_view](accelerator-view-class.md)。|  
|[synchronize_to_async](#synchronize_to_async)|以非同步方式同步處理所做的任何修改`array_view`到指定的物件[accelerator_view](accelerator-view-class.md)。|  
|[view_as](#view_as)|會產生`array_view`不同陣序，使用這個物件`array_view`物件的資料。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[operator （)](#operator_call)|傳回值的參數或參數所指定的項目。|  
|[operator]](#operator_at)|傳回參數所指定的項目。|  
|[operator=](#operator_eq)|將指定的內容複製`array_view`成這一個物件。|  
  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[rank 常數](#rank)|儲存的陣序`array_view`物件。|  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[extent](#extent)|取得定義 `extent` 物件形狀的 `array_view` 物件。|  
|[source_accelerator_view](#source_accelerator_view)|取得[accelerator_view](accelerator-view-class.md)其中的資料來源的`array_view`位於|  
|[value_type](#value_type)|實值型別`array_view`和繫結的陣列。|  
  
## <a name="remarks"></a>備註  
 `array_view`類別代表包含在資料檢視[陣列](array-class.md)物件或子區段的`array`物件。  
  
 您可以存取`array_view`物件所在的來源資料 （本機），或在不同的快速鍵或連貫性網域 （遠端）。 當您從遠端存取物件時，檢視已複製，並視快取。 除了自動快取的影響`array_view`物件有類似的效能設定檔`array`物件。 透過檢視存取資料時，會對輕微的效能帶來負面影響。  
  
 有三個遠端的使用案例︰  
  
-   藉由傳遞到系統的記憶體指標的檢視[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)加速器而且加速器上存取。  
  
-   藉由傳遞陣列位於加速器檢視`parallel_for_each`呼叫另一個快速鍵，並且那里存取。  
  
-   在 CPU 上存取陣列位於加速器上檢視。  
  
 任何一種這些案例中，參考的檢視由執行階段複製到遠端位置和修改所呼叫`array_view`物件，則會複製到本機位置。 執行階段可能會將最佳化複製回變更的程序、 可能複製只變更的元素，或可能會同時複製不變的部分。 重疊`array_view`上一個資料來源的物件不保證會維持在遠端位置的參考完整性。  
  
 您必須同步處理的任何多執行緒的存取相同的資料來源。  
  
 執行階段並快取中的資料有關的下列保證`array_view`物件︰  
  
-   良好的同步處理存取`array`物件和`array_view`程式順序中的物件在其上遵守序列發生-關聯性之前。  
  
-   重疊的所有格式已同步處理存取`array_view`上相同的快速鍵對應，針對單一物件`array`物件是透過別名`array`物件。 它們誘使總和，就會發生-之前遵守程式的順序關聯性。 沒有快取。 如果`array_view`不同加速器上執行的物件、 存取的順序並未定義，建立競爭情形。  
  
 當您建立`array_view`物件使用的指標，在系統記憶體中，您必須變更檢視`array_view`物件只能透過`array_view`指標。 或者，您必須呼叫`refresh()`其中`array_view`物件附加至系統的指標，如果基礎原生記憶體而不是透過直接變更`array_view`物件。  
  
 下列其中一個動作通知`array_view`物件會變更基礎原生記憶體和位於加速器任何複本已過時。 如果您遵循這些指導方針，指標為基礎的檢視是相同的物件提供給檢視的資料平行陣列。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `_Array_view_shape`  
  
 `_Array_view_base`  
  
 `array_view`  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  
  
##  <a name="dtor"></a>~ array_view 

 終結`array_view`物件。  
  
```  
~array_view()restrict(amp,cpu);
```  
  
##  <a name="ctor"></a>array_view 

 初始化 `array_view` 類別的新執行個體。  
  
```  
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view& _Other)restrict(amp,cpu);

 
explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    _Container& _Src) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    _Container& _Src) restrict(cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2) __CPU_ONLY;  
 
template <
    typename _Container  
>  
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _Container& _Src);

 
explicit array_view(
    int _E0,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
explicit array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    _In_ value_type* _Src)restrict(amp,cpu);

 
array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

 
array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const _Container& _Src) restrict(cpu);

 
template <
    typename _Container  
>  
explicit array_view(
    const _Container& _Src,  
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

 
array_view(
    const Concurrency::extent<_Rank>& _Extent,  
    const value_type* _Src)restrict(amp,cpu);

 
template <
    typename _Arr_type,  
    int _Size  
>  
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    const _Container& _Src);

 
template <
    typename _Container  
>  
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const _Container& _Src);

 
array_view(
    int _E0,  
    const value_type* _Src)restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    const value_type* _Src) restrict(amp,cpu);

 
array_view(
    int _E0,  
    int _E1,  
    int _E2,  
    const value_type* _Src) restrict(amp,cpu);

 
```  
  
### <a name="parameters"></a>參數  
 `_Arr_type`  
 從中提供資料的 c-style 陣列元素類型。  
  
 `_Container`  
 必須指定為線性的容器，支援的樣板引數`data()`和`size()`成員。  
  
 `_E0`  
 這個區段的範圍的最重要的元件。  
  
 `_E1`  
 本章節的範圍下一步-到-最高有效的元件。  
  
 `_E2`  
 本章節的範圍最不重要的元件。  
  
 `_Extent`  
 每個維度中的延伸區`array_view`。  
  
 `_Other`  
 型別的物件`array_view<T,N>`從中初始化新`array_view`。  
  
 `_Size`  
 從中提供資料的 c-style 陣列的大小。  
  
 `_Src`  
 來源資料，將會複製到新的陣列指標。  
  
##  <a name="copy_to"></a>copy_to 

 複製的內容`array_view`物件與指定的目的地物件，藉由呼叫`copy(*this, dest)`。  
  
```  
void copy_to(
    array<value_type, _Rank>& _Dest) const;

 
 
void copy_to(
    array_view<value_type, _Rank>& _Dest) const;

 
```  
  
### <a name="parameters"></a>參數  
 `_Dest`  
 要複製到的物件。  
  
##  <a name="data"></a>資料 

 讓指標回到的未經處理資料`array_view`。  
  
```  
value_type* data() const restrict(amp,
    cpu);

 
const value_type* data() const restrict(amp,
    cpu);
```  
  
### <a name="return-value"></a>傳回值  
 未經處理資料的指標`array_view`。  
  
##  <a name="discard_data"></a>discard_data 

 捨棄目前的資料，此檢視的基礎。 這是用來避免將目前檢視的內容複製到目標為執行階段最佳化提示`accelerator_view`存取，並不需要現有的內容時，建議使用。 這個方法不沒有任何作業時使用 restrict （amp） 內容中  
  
```  
void discard_data() const restrict(cpu);
```  
  
##  <a name="extent"></a>範圍 

 取得定義 `extent` 物件形狀的 `array_view` 物件。  
  
```  
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;  
```  
  
##  <a name="get_extent"></a>get_extent 

 傳回[範圍](extent-class.md)物件`array_view`物件。  
  
```  
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```  
  
### <a name="return-value"></a>傳回值  
 `extent`物件`array_view`物件  
  
##  <a name="get_ref"></a>get_ref 

 取得由 _Index 編製索引的項目參考。 不同於其他索引運算子來存取在 CPU 上的 array_view，這個方法不會隱含地同步此 array_view 內容的 cpu。 存取遠端位置上的 array_view 或執行複製作業，涉及此 array_view 之後，使用者要負責明確地呼叫這個方法之前同步處理的 cpu array_view。 若要這樣做導致未定義的行為。  
  
```  
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 索引。  
  
### <a name="return-value"></a>傳回值  
 以 _Index 編製索引的項目參考  
  
##  <a name="get_source_accelerator_view"></a>get_source_accelerator_view 

 傳回 accelerator_view array_view 的資料來源所在的位置。 如果 array_view 並沒有資料來源，此 API 會擲回 runtime_exception  
  
```  
accelerator_view get_source_accelerator_view() const;

 
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="operator_call"></a>operator （) 

 傳回值的參數或參數所指定的項目。  
  
```  
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1) const restrict(amp,cpu);

 
value_type& operator() (
    int _I0,  
    int _I1,  
    int _I2) const restrict(amp,cpu);

 
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 項目的位置。  
  
 `_I0`  
 中的第一個維度的索引。  
  
 `_I1`  
 第二個維度中的索引。  
  
 `_I2`  
 第三個維度中的索引。  
  
 `_I`  
 項目的位置。  
  
### <a name="return-value"></a>傳回值  
 元素所指定的參數或參數的值。  
  
##  <a name="operator_at"></a>operator] 

 傳回參數所指定的項目。  
  
```  
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

 
value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 索引。  
  
 `_I`  
 索引。  
  
### <a name="return-value"></a>傳回值  
 索引處的項目值或`array_view`投影最有效的維度上。  
  
##  <a name="operator_eq"></a>運算子 = 

 將指定的內容複製`array_view`給這一個物件。  
  
```  
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

 
array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `array_view`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`array_view`物件。  
  
##  <a name="rank"></a>順位 

 儲存的陣序`array_view`物件。  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="refresh"></a>重新整理 

 通知`array_view`其繫結的記憶體外部修改過的物件`array_view`介面。 呼叫這個方法會轉譯過時所有快取的資訊。  
  
```  
void refresh() const restrict(cpu);
```  
## <a name="reinterpret_as"></a>reinterpret_as 

轉換到一維 array_view，它做為選項可以有不同的值型別比來源 array_view array_view。  
  
### <a name="syntax"></a>語法  
  
```  
template <  
    typename _Value_type2  
>  
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
  
template <  
    typename _Value_type2  
>  
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Value_type2`  
 新的資料型別`array_view`物件。  
  
### <a name="return-value"></a>傳回值  
 `array_view`物件或 const`array_view`物件，這根據`array_view`，從轉換的項目類型與`T`至`_Value_type2`，和等級從降低*N*設為 1。  
  
### <a name="remarks"></a>備註  
 有時候很方便檢視線性的一維陣列，這可能會有不同的值型別比來源陣列為多維陣列。 您也可以達到這個目的在`array_view`使用此方法。  
  
**警告**Reinterpeting array_view 物件使用不同的值類型是可能不安全的作業。 這項功能應該小心使用。  
  
 以下為範例：  
  
```cpp  
struct RGB { float r; float g; float b; };  
  
array<RGB,3>  a = ...;   
array_view<float,1> v = a.reinterpret_as<float>();   
  
assert(v.extent == 3*a.extent);  
```  
    
##  <a name="section"></a>區段 

 傳回的子區段`array_view`物件位於指定的來源，並選擇性地，具有指定的範圍。  
  
```  
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,  
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

 
array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _E0) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _E0,  
    int _E1) const restrict(amp,cpu);

 
array_view section(
    int _I0,  
    int _I1,  
    int _I2,  
    int _E0,  
    int _E1,  
    int _E2) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_E0`  
 這個區段的範圍的最重要的元件。  
  
 `_E1`  
 本章節的範圍下一步-到-最高有效的元件。  
  
 `_E2`  
 本章節的範圍最不重要的元件。  
  
 `_Ext`  
 [範圍](extent-class.md)物件，指定區段的範圍。 原點是 0。  
  
 `_Idx`  
 [索引](index-class.md)物件，指定的來源位置。 子區段是範圍的其餘部分。  
  
 `_I0`  
 本章節的原點最重要的元件。  
  
 `_I1`  
 本章節的原點下一步-到-最高有效的元件。  
  
 `_I2`  
 本章節的原點最不重要的元件。  
  
 `_Rank`  
 區段的陣序規範。  
  
 `_Section_extent`  
 [範圍](extent-class.md)物件，指定區段的範圍。  
  
 `_Section_origin`  
 [索引](index-class.md)物件，指定的來源位置。  
  
### <a name="return-value"></a>傳回值  
 子區段的`array_view`物件位於指定的來源，並選擇性地，具有指定的範圍。 只有當`index`指定的物件、 小節包含有索引大於索引中的項目與相關聯的範圍中所有項目`index`物件。  
  
##  <a name="source_accelerator_view"></a>source_accelerator_view 

 取得此 array_view 聯來源 accelerator_view。  
  
```  
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;  
```  
  
##  <a name="synchronize"></a>同步處理 

 同步處理所做的任何修改`array_view`回到其來源資料的物件。  
  
```  
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize() const restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Access_type`  
 所需的[access_type](concurrency-namespace-enums-amp.md#access_type)目標上[accelerator_view](accelerator-view-class.md)。 此參數有預設值是`access_type_read`。  
  
##  <a name="synchronize_async"></a>synchronize_async 

 以非同步方式同步處理所做的任何修改`array_view`回到其來源資料的物件。  
  
```  
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_async() const restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Access_type`  
 所需的[access_type](concurrency-namespace-enums-amp.md#access_type)目標上[accelerator_view](accelerator-view-class.md)。 此參數有預設值是`access_type_read`。  
  
### <a name="return-value"></a>傳回值  
 在未來的等候作業完成。  
  
##  <a name="synchronize_to"></a>synchronize_to 

 同步處理對這個 array_view 來指定 accelerator_view 任何修改。  
  
```  
void synchronize_to(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Accl_view`  
 同步處理至目標 accelerator_view。  
  
 `_Access_type`  
 在目標 accelerator_view 上所需的 access_type。 此參數有預設值是 access_type_read。  
  
##  <a name="synchronize_to_async"></a>synchronize_to_async 

 以非同步方式同步處理對這個 array_view 來指定 accelerator_view 任何修改。  
  
```  
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,  
    access_type _Access_type = access_type_read) const restrict(cpu);

 
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```  
  
### <a name="parameters"></a>參數  
 `_Accl_view`  
 同步處理至目標 accelerator_view。  
  
 `_Access_type`  
 在目標 accelerator_view 上所需的 access_type。 此參數有預設值是 access_type_read。  
  
### <a name="return-value"></a>傳回值  
 在未來的等候作業完成。  
  
##  <a name="value_type"></a>value_type 

 Array_view 值類型的繫結的陣列。  
  
```  
typedef typenamevalue_type value_type;  
```  
  
##  <a name="view_as"></a>view_as 

 此轉換`array_view`為`array_view`不同陣序規範。  
  
```  
template <
    int _New_rank  
>  
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

 
template <
    int _New_rank  
>  
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```  
  
### <a name="parameters"></a>參數  
 `_New_rank`  
 新的陣序規範`array_view`物件。  
  
 `_View_extent`  
 才可遏制`extent`。  
  
 `value_type`  
 資料類型中兩個原始的項目[陣列](array-class.md)物件並傳回`array_view`物件。  
  
### <a name="return-value"></a>傳回值  
 `array_view`建構物件。  
  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)


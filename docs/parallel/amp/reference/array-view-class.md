---
title: array_view 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: e73639ffd11e08edb2fdb03471f2c6c88730f02d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405556"
---
# <a name="arrayview-class"></a>array_view 類別

代表 N 維檢視一段保留另一個容器中的資料。

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

*value_type*<br/>
資料類型中的項目`array_view`物件。

*_Rank*<br/>
陣序`array_view`物件。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[array_view 建構函式](#ctor)|初始化 `array_view` 類別的新執行個體。 沒有任何預設建構函式`array<T,N>`。 所有建構函式會限制為只能在 CPU 上執行，而且無法在 Direct3D 目標上執行。|
|[~ array_view 解構函式](#ctor)|終結`array_view`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[copy_to](#copy_to)|複製的內容`array_view`藉由呼叫指定的目的地物件`copy(*this, dest)`。|
|[data](#data)|傳回的未經處理資料的指標`array_view`。|
|[discard_data](#discard_data)|捨棄目前的資料，此檢視的基礎。|
|[get_extent](#get_extent)|傳回 array_view 物件的物件的範圍。|
|[get_ref](#get_ref)|傳回的參考索引項目。|
|[get_source_accelerator_view](#get_source_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)其中的資料來源`array_view`所在。|
|[refresh](#refresh)|會告知`array_view`繫結的記憶體已外修改過的物件`array_view`介面。 此方法的呼叫會轉譯過時所有快取的資訊。|
|[reinterpret_as](#reinterpret_as)|傳回一維陣列，包含中的所有項目`array_view`物件。|
|[section](#section)|傳回的子區段`array_view`物件位於指定的來源，並選擇性地，具有指定的範圍。|
|[synchronize](#synchronize)|若要進行任何修改同步處理`array_view`回到其來源資料的物件。|
|[synchronize_async](#synchronize_async)|以非同步方式同步處理任何所做的修改`array_view`回到其來源資料的物件。|
|[synchronize_to](#synchronize_to)|若要進行任何修改同步處理`array_view`至指定的物件[accelerator_view](accelerator-view-class.md)。|
|[synchronize_to_async](#synchronize_to_async)|以非同步方式進行任何修改同步處理`array_view`至指定的物件[accelerator_view](accelerator-view-class.md)。|
|[view_as](#view_as)|會產生`array_view`物件，使用此為不同陣序`array_view`物件的資料。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator()](#operator_call)|傳回的值或多個參數所指定的項目。|
|[operator\[\]](#operator_at)|傳回參數所指定的項目。|
|[operator=](#operator_eq)|將指定的內容複製`array_view`到這個物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|儲存的陣序`array_view`物件。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[extent](#extent)|取得定義 `extent` 物件形狀的 `array_view` 物件。|
|[source_accelerator_view](#source_accelerator_view)|取得[accelerator_view](accelerator-view-class.md)其中的資料來源`array_view`位於|
|[value_type](#value_type)|實值型別`array_view`和繫結的陣列。|

## <a name="remarks"></a>備註

`array_view`類別代表包含在資料檢視[陣列](array-class.md)物件或子區段的`array`物件。

您可以存取`array_view`物件所在的來源資料 （本機），或在不同的加速器或連貫網域 （遠端）。 當您從遠端存取的物件時，檢視複製，並視快取。 除了自動快取的效果`array_view`物件具有類似的效能設定檔`array`物件。 當您透過檢視存取資料時，沒有對小小的效能產生負面影響。

有三個遠端使用情節：

- 系統記憶體指標的檢視藉由傳遞[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)呼叫至加速器，並在加速器上存取。

- 位於加速器之陣列檢視藉由傳遞`parallel_for_each`呼叫另一個加速器，並在那裡進行存取。

- 位於加速器之陣列檢視是在 CPU 上存取。

在任何一種情況下，將參考的檢視由執行階段複製到遠端位置，如果修改呼叫`array_view`物件，會複製回本機位置。 執行階段可能會最佳化重新複製變更的程序，可能會複製只變更的元素，或也可能會複製未變更的部分。 重疊`array_view`不保證維護參考完整性，在遠端位置上一個資料來源的物件。

您必須同步處理任何多執行緒的存取相同的資料來源。

執行階段做出下列有關快取中的資料保證`array_view`物件：

- 所有適當同步存取`array`物件和`array_view`物件在其上的依照程式順序會遵循序列發生-關聯性。

- 重疊的所有適當同步存取`array_view`單一對相同加速器上的物件`array`物件會透過別名`array`物件。 它們會引發，就會發生-關聯性會遵守程式順序。 沒有快取。 如果`array_view`物件不同的加速器上執行，則存取順序尚未定義，建立競爭條件。

當您建立`array_view`物件使用的指標，在系統記憶體中，您必須變更檢視`array_view`只能透過`array_view`指標。 或者，您必須呼叫`refresh()`上的其中一個`array_view`物件附加至系統指標，如果基礎原生記憶體直接變更，而不是透過`array_view`物件。

任一動作都會告知`array_view`物件，會變更基礎原生記憶體和任何位於加速器的複本會過期。 如果您遵循這些指導方針，指標為基礎的檢視是提供給資料平行陣列檢視相同的。

## <a name="inheritance-hierarchy"></a>繼承階層

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

##  <a name="dtor"></a> ~array_view

終結`array_view`物件。

```
~array_view()restrict(amp,cpu);
```

##  <a name="ctor"></a> array_view

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

*_Arr_type*<br/>
提供資料之 c-style 陣列的項目型別。

*_Container*<br/>
必須指定支援的線性容器的樣板引數`data()`和`size()`成員。

*_E0*<br/>
這個區段範圍的最重要的元件。

*_E1*<br/>
這個區段範圍的下一步 以-重要元件。

*_E2*<br/>
這個區段範圍的最不重要元件。

*_Extent*<br/>
每個維度中的延伸區`array_view`。

*_Other*<br/>
型別的物件`array_view<T,N>`從中初始化新`array_view`。

*_Size*<br/>
提供資料之 c-style 陣列的大小。

*_Src*<br/>
來源資料，將會複製到新的陣列指標。

##  <a name="copy_to"></a> copy_to

複製的內容`array_view`物件與指定的目的地物件，藉由呼叫`copy(*this, dest)`。

```
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要複製到的物件。

##  <a name="data"></a> data

傳回的未經處理資料的指標`array_view`。

```
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>傳回值

未經處理資料的指標`array_view`。

##  <a name="discard_data"></a> discard_data

捨棄目前的資料，此檢視的基礎。 這是用來避免將目前檢視的內容複製到目標執行階段的最佳化提示`accelerator_view`存取，且如果不需要現有的內容，則建議使用。 這個方法不會執行任何作業時用於 restrict （amp） 內容

```
void discard_data() const restrict(cpu);
```

##  <a name="extent"></a> 範圍

取得定義 `extent` 物件形狀的 `array_view` 物件。

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_extent"></a> get_extent

傳回[程度](extent-class.md)物件的`array_view`物件。

```
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>傳回值

`extent`物件的`array_view`物件

##  <a name="get_ref"></a> get_ref

取得依據 _index 索引之項目的參考。 不同於其他索引運算子來存取 CPU 的 array_view，這個方法不會隱含地同步處理這個 array_view 內容給 CPU。 存取遠端位置上的 array_view 或執行與此 array_view 相關的複製作業後使用者必須負責明確同步處理之前呼叫這個方法的陣列檢視與 CPU。 若要這樣做的失敗會導致未定義的行為。

```
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

### <a name="return-value"></a>傳回值

依據 _Index 索引之項目的參考

##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view

傳回 array_view 資料來源所在位置的 accelerator_view。 如果 array_view 沒有資料來源，此 API 會擲回 runtime_exception

```
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>傳回值

##  <a name="operator_call"></a> operator()

傳回的值或多個參數所指定的項目。

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

*_Index*<br/>
項目的位置。

*_I0*<br/>
中的第一個維度的索引。

*_I1*<br/>
第二個維度中的索引。

*_I2*<br/>
第三個維度中的索引。

*_I*<br/>
項目的位置。

### <a name="return-value"></a>傳回值

元素所指定的參數或參數的值。

##  <a name="operator_at"></a> operator[]

傳回參數所指定的項目。

```
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

*_I*<br/>
索引。

### <a name="return-value"></a>傳回值

在索引中，元素的值或`array_view`投影在最高有效維度。

##  <a name="operator_eq"></a> 運算子 =

將指定的內容複製`array_view`如下的物件。

```
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`array_view`從複製的物件。

### <a name="return-value"></a>傳回值

此參考`array_view`物件。

##  <a name="rank"></a> 陣序規範

儲存的陣序`array_view`物件。

```
static const int rank = _Rank;
```

##  <a name="refresh"></a> 重新整理

會告知`array_view`繫結的記憶體已外修改過的物件`array_view`介面。 此方法的呼叫會轉譯過時所有快取的資訊。

```
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a> reinterpret_as

重新解譯 array_view 透過一維 array_view，可以有不同於實值類型來源 array_view 的選項。

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

*_Value_type2*<br/>
新的資料型別`array_view`物件。

### <a name="return-value"></a>傳回值

`array_view`物件或常數`array_view`物件，這根據`array_view`，與從轉換的項目型別`T`來`_Value_type2`，且從*N*為 1。

### <a name="remarks"></a>備註

有時候很方便檢視多維陣列當做線性一維陣列，可能會有不同的實值型別，於來源陣列。 您也可以達到此目的在`array_view`使用此方法。

**警告**重新解譯 array_view 物件使用不同的實值型別是可能不安全的作業。 應該謹慎使用這項功能。

以下為範例：

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> 區段

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

*_E0*<br/>
這個區段範圍的最重要的元件。

*_E1*<br/>
這個區段範圍的下一步 以-重要元件。

*_E2*<br/>
這個區段範圍的最不重要元件。

*_Ext*<br/>
[範圍](extent-class.md)指定區段範圍的物件。 原點是 0。

*_Idx*<br/>
[Index](index-class.md)物件，指定原點的位置。 子區段是範圍的其餘部分。

*_I0*<br/>
本節的原點的最重要的元件。

*_I1*<br/>
下一步-至-重要元件之原點的這一節。

*_I2*<br/>
本節中的來源最不重要元件。

*_Rank*<br/>
區段的順位。

*_Section_extent*<br/>
[範圍](extent-class.md)指定區段範圍的物件。

*_Section_origin*<br/>
[Index](index-class.md)物件，指定原點的位置。

### <a name="return-value"></a>傳回值

子區段`array_view`物件位於指定的來源，並選擇性地，具有指定的範圍。 當只有`index`指定的物件，子區段會包含所有相關聯的範圍中的元素，其大於中的項目索引的索引`index`物件。

##  <a name="source_accelerator_view"></a> source_accelerator_view

取得這個 array_view 相關聯的來源 accelerator_view。

```
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

##  <a name="synchronize"></a> 同步處理

若要進行任何修改同步處理`array_view`回到其來源資料的物件。

```
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Access_type*<br/>
預期[access_type](concurrency-namespace-enums-amp.md#access_type)目標上[accelerator_view](accelerator-view-class.md)。 此參數的預設值是`access_type_read`。

##  <a name="synchronize_async"></a> synchronize_async

以非同步方式同步處理任何所做的修改`array_view`回到其來源資料的物件。

```
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Access_type*<br/>
預期[access_type](concurrency-namespace-enums-amp.md#access_type)目標上[accelerator_view](accelerator-view-class.md)。 此參數的預設值是`access_type_read`。

### <a name="return-value"></a>傳回值

要等候作業完成的未來。

##  <a name="synchronize_to"></a> synchronize_to

對此 array_view 物件至指定的 accelerator_view 進行任何修改同步處理。

```
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Accl_view*<br/>
同步處理至目標 accelerator_view。

*_Access_type*<br/>
目標 accelerator_view 上所需的 access_type。 此參數有預設值為 access_type_read。

##  <a name="synchronize_to_async"></a> synchronize_to_async

以非同步方式將對此 array_view 物件至指定的 accelerator_view 進行任何修改都同步處理。

```
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Accl_view*<br/>
同步處理至目標 accelerator_view。

*_Access_type*<br/>
目標 accelerator_view 上所需的 access_type。 此參數有預設值為 access_type_read。

### <a name="return-value"></a>傳回值

要等候作業完成的未來。

##  <a name="value_type"></a> value_type

Array_view 和繫結的陣列的實值型別。

```
typedef typenamevalue_type value_type;
```

##  <a name="view_as"></a> view_as

重新解譯此`array_view`做為`array_view`為不同陣序。

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

*_New_rank*<br/>
新的陣序`array_view`物件。

*_View_extent*<br/>
形狀`extent`。

*value_type*<br/>
這兩個原始項目的資料型別[陣列](array-class.md)物件，並傳回`array_view`物件。

### <a name="return-value"></a>傳回值

`array_view`建構的物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

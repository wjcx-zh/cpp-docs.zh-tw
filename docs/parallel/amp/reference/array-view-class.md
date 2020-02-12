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
ms.openlocfilehash: 2aef75eedcde2a2064fe12815d9afd21fee2c293
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127133"
---
# <a name="array_view-class"></a>array_view 類別

代表保留在另一個容器中之資料的 N 維視圖。

## <a name="syntax"></a>語法

```cpp
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

### <a name="parameters"></a>參數

*value_type*<br/>
`array_view` 物件中元素的資料類型。

*_Rank*<br/>
`array_view` 物件的順位。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[array_view 的構造函式](#ctor)|初始化 `array_view` 類別的新執行個體。 `array<T,N>`沒有預設的構造函式。 所有的函式僅限於在 CPU 上執行，且無法在 Direct3D 目標上執行。|
|[~ array_view 的析構函式](#ctor)|終結 `array_view` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[copy_to](#copy_to)|藉由呼叫 `copy(*this, dest)`，將 `array_view` 物件的內容複寫到指定的目的地。|
|[data](#data)|傳回 `array_view`原始資料的指標。|
|[discard_data](#discard_data)|捨棄此視圖基礎的目前資料。|
|[get_extent](#get_extent)|傳回 array_view 物件的範圍物件。|
|[get_ref](#get_ref)|傳回索引元素的參考。|
|[get_source_accelerator_view](#get_source_accelerator_view)|傳回 `array_view` 的資料來源所在的[accelerator_view](accelerator-view-class.md) 。|
|[恢復](#refresh)|通知 `array_view` 物件已在 `array_view` 介面外部修改其系結記憶體。 呼叫這個方法會將所有快取的資訊呈現為過時。|
|[reinterpret_as](#reinterpret_as)|傳回一維陣列，其中包含 `array_view` 物件中的所有元素。|
|[section](#section)|傳回位於指定之來源之 `array_view` 物件的子區段，並選擇性地傳回具有指定範圍的。|
|[synchronize](#synchronize)|將對 `array_view` 物件所做的任何修改同步處理回其來源資料。|
|[synchronize_async](#synchronize_async)|以非同步方式將對 `array_view` 物件所做的任何修改同步處理回其來源資料。|
|[synchronize_to](#synchronize_to)|將對 `array_view` 物件所做的任何修改同步處理至指定的[accelerator_view](accelerator-view-class.md)。|
|[synchronize_to_async](#synchronize_to_async)|以非同步方式將對 `array_view` 物件所做的任何修改同步處理至指定的[accelerator_view](accelerator-view-class.md)。|
|[view_as](#view_as)|使用這個 `array_view` 物件的資料，產生不同次序的 `array_view` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator()](#operator_call)|傳回由參數或參數指定的元素值。|
|[operator\[\]](#operator_at)|傳回參數所指定的元素。|
|[operator=](#operator_eq)|將指定 `array_view` 物件的內容複寫到這個。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[次序常數](#rank)|儲存 `array_view` 物件的順位。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[extent](#extent)|取得定義 `extent` 物件形狀的 `array_view` 物件。|
|[source_accelerator_view](#source_accelerator_view)|取得 `array_view` 資料來源所在的[accelerator_view](accelerator-view-class.md)|
|[value_type](#value_type)|`array_view` 和系結陣列的實值型別。|

## <a name="remarks"></a>備註

`array_view` 類別代表包含在[陣列](array-class.md)物件或 `array` 物件子區段中之資料的視圖。

您可以存取來源資料所在的 `array_view` 物件（本機）或不同的加速器或連貫性網域（遠端）。 當您從遠端存取物件時，會視需要複製和快取 views。 除了自動快取的效果，`array_view` 物件的效能設定檔類似 `array` 物件。 當您透過 views 存取資料時，會有些許效能的負面影響。

有三種遠端使用案例：

- 系統記憶體指標的視圖會透過對加速器的[parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)呼叫來傳遞，並在加速器上存取。

- 位於快速鍵上之陣列的視圖會透過對另一個快速鍵的 `parallel_for_each` 呼叫來傳遞，並在該處存取。

- 對位於加速器上之陣列的視圖，會在 CPU 上存取。

在上述任何一種情況中，參考的視圖都會由執行時間複製到遠端位置，而如果由 `array_view` 物件的呼叫所修改，則會複製回本機位置。 執行時間可能會優化複製變更的程式，可能只複製已變更的元素，或者也可能複製不變的部分。 在某個資料來源上重迭的 `array_view` 物件不保證會在遠端位置維護參考完整性。

您必須同步處理相同資料來源的任何多執行緒存取。

執行時間會針對 `array_view` 物件中的資料快取提供下列保證：

- 在關聯性之前，會依照程式順序，對 `array` 物件和其上的 `array_view` 物件進行所有已妥善同步的存取，以遵循序列。

- 在單一 `array` 物件上，對相同加速器上重迭的 `array_view` 物件進行的所有妥善同步存取，都是透過 `array` 物件進行別名處理。 它們會引發 total 遵守程式順序的關聯性。 沒有快取。 如果 `array_view` 物件是在不同的加速器上執行，則不會定義存取順序，而是建立競爭條件。

當您使用系統記憶體中的指標建立 `array_view` 物件時，您必須只透過 `array_view` 指標變更 view `array_view` 物件。 或者，如果基礎原生記憶體直接變更，而不是透過 `array_view` 物件，則您必須在附加至系統指標的其中一個 `array_view` 物件上呼叫 `refresh()`。

任一動作都會通知 `array_view` 物件，基礎原生記憶體已變更，且位於快速鍵上的任何複本已過期。 如果您遵循這些指導方針，以指標為基礎的視圖與提供給資料平行陣列的視圖相同。

## <a name="inheritance-hierarchy"></a>繼承階層

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="dtor"></a>~ array_view

終結 `array_view` 物件。

```cpp
~array_view()restrict(amp,cpu);
```

## <a name="ctor"></a>array_view

初始化 `array_view` 類別的新執行個體。

```cpp
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
提供資料之 C 樣式陣列的元素類型。

*_Container*<br/>
範本引數，必須指定支援 `data()` 和 `size()` 成員的線性容器。

*_E0*<br/>
本節範圍中最重要的元件。

*_E1*<br/>
這個區段範圍的下一個最重要的元件。

*_E2*<br/>
本節範圍中最重要的元件。

*_Extent*<br/>
此 `array_view`之每個維度中的範圍。

*_Other*<br/>
類型的物件，`array_view<T,N>` 從中初始化新的 `array_view`。

*_Size*<br/>
提供資料之 C 樣式陣列的大小。

*_Src*<br/>
將複製到新陣列中之來源資料的指標。

## <a name="copy_to"></a>copy_to

藉由呼叫 `copy(*this, dest)`，將 `array_view` 物件的內容複寫到指定的目的地物件。

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要複製的物件。

## <a name="data"></a>data

傳回 `array_view`原始資料的指標。

```cpp
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>傳回值

`array_view`之原始資料的指標。

## <a name="discard_data"></a>discard_data

捨棄此視圖基礎的目前資料。 這是執行時間的優化提示，用於避免將目前的視圖內容複寫到其所存取的目標 `accelerator_view`，如果不需要現有的內容，則建議使用此選項。 在限制（amp）內容中使用時，這個方法不是 op

```cpp
void discard_data() const restrict(cpu);
```

## <a name="extent"></a>片區

取得定義 `extent` 物件形狀的 `array_view` 物件。

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_extent"></a>get_extent

傳回 `array_view` 物件的[範圍](extent-class.md)物件。

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>傳回值

`array_view` 物件的 `extent` 物件

## <a name="get_ref"></a>get_ref

取得以 _Index 編制索引之元素的參考。 不同于用來存取 CPU array_view 的其他索引運算子，此方法不會將此 array_view 的內容隱含地同步處理到 CPU。 存取遠端位置上的 array_view 或執行與此 array_view 的複製作業之後，使用者會負責在呼叫這個方法之前，將 array_view 明確地同步處理到 CPU。 如果無法這麼做，會導致未定義的行為。

```cpp
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

### <a name="return-value"></a>傳回值

參考所編制索引的元素 _Index

## <a name="get_source_accelerator_view"></a>get_source_accelerator_view

傳回 array_view 的資料來源所在的 accelerator_view。 如果 array_view 沒有資料來源，則此 API 會擲回 runtime_exception

```cpp
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>傳回值

## <a name="operator_call"></a>operator （）

傳回由參數或參數指定的元素值。

```cpp
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
元素的位置。

*_I0*<br/>
第一個維度中的索引。

*_I1*<br/>
第二個維度中的索引。

*_I2*<br/>
第三個維度中的索引。

*_I*<br/>
元素的位置。

### <a name="return-value"></a>傳回值

參數或參數所指定的元素值。

## <a name="operator_at"></a>operator []

傳回參數所指定的元素。

```cpp
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

位於索引的專案值，或投射在最重要維度上的 `array_view`。

## <a name="operator_eq"></a>operator =

將指定之 `array_view` 物件的內容複寫到這個。

```cpp
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源 `array_view` 物件。

### <a name="return-value"></a>傳回值

這個 `array_view` 物件的參考。

## <a name="rank"></a>等級

儲存 `array_view` 物件的順位。

```cpp
static const int rank = _Rank;
```

## <a name="refresh"></a>恢復

通知 `array_view` 物件已在 `array_view` 介面外部修改其系結記憶體。 呼叫這個方法會將所有快取的資訊呈現為過時。

```cpp
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a>reinterpret_as

透過一維 array_view 向量 array_view，其選項可以具有與來源 array_view 不同的實數值型別。

### <a name="syntax"></a>語法

```cpp
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
新 `array_view` 物件的資料類型。

### <a name="return-value"></a>傳回值

以這個 `array_view`為基礎的 `array_view` 物件或 const `array_view` 物件，其專案類型會從 `T` 轉換成 `_Value_type2`，而次序則從*N*縮減為1。

### <a name="remarks"></a>備註

有時候，將多維陣列視為線性的一維陣列，可能會有與來源陣列不同的實數值型別，這是很方便的方式。 您可以使用這個方法，在 `array_view` 上達成此目的。

**警告**使用不同的實數值型別來別的 array_view 物件是可能不安全的作業。 此功能應謹慎使用。

以下是範例：

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>截面

傳回位於指定之來源之 `array_view` 物件的子區段，並選擇性地傳回具有指定範圍的。

```cpp
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
本節範圍中最重要的元件。

*_E1*<br/>
這個區段範圍的下一個最重要的元件。

*_E2*<br/>
本節範圍中最重要的元件。

*_Ext*<br/>
[範圍](extent-class.md)物件，指定區段的範圍。 來源為0。

*_Idx*<br/>
指定來源位置的[索引](index-class.md)物件。 小節是範圍的其餘部分。

*_I0*<br/>
這一節的最重要元件。

*_I1*<br/>
這個區段的下一個最重要的元件。

*_I2*<br/>
這一節的最重要元件。

*_Rank*<br/>
區段的順位。

*_Section_extent*<br/>
[範圍](extent-class.md)物件，指定區段的範圍。

*_Section_origin*<br/>
指定來源位置的[索引](index-class.md)物件。

### <a name="return-value"></a>傳回值

位於指定之來源且選擇性地具有指定範圍之 `array_view` 物件的子區段。 只有在指定 `index` 物件時，子區段會包含相關聯之範圍中的所有專案，這些專案的索引大於 `index` 物件中的元素索引。

## <a name="source_accelerator_view"></a>source_accelerator_view

取得與此 array_view 相關聯的來源 accelerator_view。

```cpp
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

## <a name="synchronize"></a>同步處理

將對 `array_view` 物件所做的任何修改同步處理回其來源資料。

```cpp
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Access_type*<br/>
目標[accelerator_view](accelerator-view-class.md)上的預期[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此參數的預設值為 `access_type_read`。

## <a name="synchronize_async"></a>synchronize_async

以非同步方式將對 `array_view` 物件所做的任何修改同步處理回其來源資料。

```cpp
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Access_type*<br/>
目標[accelerator_view](accelerator-view-class.md)上的預期[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此參數的預設值為 `access_type_read`。

### <a name="return-value"></a>傳回值

未來要等候作業完成的時間。

## <a name="synchronize_to"></a>synchronize_to

將對此 array_view 進行的任何修改同步處理至指定的 accelerator_view。

```cpp
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Accl_view*<br/>
要同步處理的目標 accelerator_view。

*_Access_type*<br/>
目標 accelerator_view 上所需的 access_type。 此參數的預設值為 access_type_read。

## <a name="synchronize_to_async"></a>synchronize_to_async

以非同步方式將對此 array_view 進行的任何修改同步處理至指定的 accelerator_view。

```cpp
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>參數

*_Accl_view*<br/>
要同步處理的目標 accelerator_view。

*_Access_type*<br/>
目標 accelerator_view 上所需的 access_type。 此參數的預設值為 access_type_read。

### <a name="return-value"></a>傳回值

未來要等候作業完成的時間。

## <a name="value_type"></a>value_type

Array_view 和系結陣列的實值型別。

```cpp
typedef typenamevalue_type value_type;
```

## <a name="view_as"></a>view_as

以不同排名的 `array_view` 向量此 `array_view`。

```cpp
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
新 `array_view` 物件的順位。

*_View_extent*<br/>
重新整形 `extent`。

*value_type*<br/>
原始[陣列](array-class.md)物件和傳回的 `array_view` 物件中專案的資料類型。

### <a name="return-value"></a>傳回值

所結構化的 `array_view` 物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

---
title: array 類別
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127108"
---
# <a name="array-class"></a>array 類別

表示用來將資料移至快速鍵的資料容器。

## <a name="syntax"></a>語法

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>參數

*value_type*<br/>
資料的元素類型。

*_Rank*<br/>
陣列的順位。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[陣列的構造函式](#ctor)|初始化 `array` 類別的新執行個體。|
|[~ 陣列的析構函式](#dtor)|終結 `array` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[copy_to](#copy_to)|將陣列的內容複寫到另一個陣列。|
|[data](#data)|傳回陣列原始資料的指標。|
|[get_accelerator_view](#get_accelerator_view)|傳回代表配置陣列位置的[accelerator_view](accelerator-view-class.md)物件。 這個屬性只能在 CPU 上存取。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|取得在呼叫暫存函式以具現化 `array` 物件時，傳遞做為參數的第二個[accelerator_view](accelerator-view-class.md)物件。|
|[get_cpu_access_type](#get_cpu_access_type)|傳回陣列的[access_type](concurrency-namespace-enums-amp.md#access_type) 。 這個方法只能在 CPU 上存取。|
|[get_extent](#get_extent)|傳回陣列的[範圍](extent-class.md)物件。|
|[reinterpret_as](#reinterpret_as)|傳回一維陣列，其中包含 `array` 物件中的所有元素。|
|[section](#section)|傳回位於指定之來源之 `array` 物件的子區段，並選擇性地傳回具有指定範圍的。|
|[view_as](#view_as)|傳回從 `array` 物件所結構化的[array_view](array-view-class.md)物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算子 std：： vector&lt;value_type&gt;](#operator_vec)|使用 `copy(*this, vector)`，將陣列隱含地轉換為 std：：[vector](../../../standard-library/vector-class.md)物件。|
|[operator()](#operator_call)|傳回參數所指定的元素值。|
|[operator\[\]](#operator_at)|傳回位於指定索引處的元素。|
|[operator=](#operator_eq)|將指定 `array` 物件的內容複寫到這個。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[次序常數](#rank)|儲存陣列的順位。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|取得代表配置陣列位置的[accelerator_view](accelerator-view-class.md)物件。 這個屬性只能在 CPU 上存取。|
|[associated_accelerator_view](#associated_accelerator_view)|取得在呼叫暫存函式以具現化 `array` 物件時，傳遞做為參數的第二個[accelerator_view](accelerator-view-class.md)物件。|
|[cpu_access_type](#cpu_access_type)|取得[access_type](concurrency-namespace-enums-amp.md#access_type) ，表示 CPU 如何存取陣列的儲存體。|
|[extent](#extent)|取得定義陣列圖形的範圍。|

## <a name="remarks"></a>備註

類型 `array<T,N>` 代表在特定位置（例如加速器或 CPU）中的密集和一般（非不規則）的*N*維陣列。 陣列中元素的資料類型是 `T`，其必須是與目標加速器相容的類型。 雖然陣列的順位、`N`（）是以靜態方式決定，而且是類型的一部分，但陣列的範圍是由執行時間所決定，而且是使用類別 `extent<N>`來表示。

陣列可以有任意數目的維度，雖然某些功能專門用於具有次序1、2和3的 `array` 物件。 如果您省略維度引數，預設值為1。

陣列資料會在記憶體中連續配置。 在最不重要的維度中，有一個不同的元素會在記憶體中相鄰。

陣列會以邏輯方式被視為實數值型別，因為當陣列複製到另一個陣列時，會執行深層複製。 兩個數組永遠不會指向相同的資料。

在數種情況下，會使用 `array<T,N>` 類型：

- 做為可用於快速鍵計算的資料容器。

- 做為保留主機 CPU 記憶體的資料容器（可用於在其他陣列之間進行複製）。

- 作為預備物件，做為主機對裝置複本的快速媒介。

## <a name="inheritance-hierarchy"></a>繼承階層

`array`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="dtor"></a>~ 陣列

終結 `array` 物件。

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

取得代表配置陣列位置的[accelerator_view](accelerator-view-class.md)物件。 這個屬性只能在 CPU 上存取。

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>數列

初始化[陣列類別](array-class.md)的新實例。 `array<T,N>`沒有預設的構造函式。 所有的函式只會在 CPU 上執行。 它們無法在 Direct3D 目標上執行。

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>參數

*_Associated_Av*<br/>
Accelerator_view，指定陣列的慣用目標位置。

*_Av*<br/>
指定陣列位置的[accelerator_view](accelerator-view-class.md)物件。

*_Cpu_access_type*<br/>
CPU 上的陣列所需的[access_type](concurrency-namespace-enums-amp.md#access_type) 。 此參數的預設值為 `access_type_auto` 保留 CPU `access_type` 判斷執行時間。 您可以使用 `get_cpu_access_type` 方法來查詢陣列的實際 CPU `access_type`。

*_Extent*<br/>
陣列的每個維度中的範圍。

*_E0*<br/>
本節範圍中最重要的元件。

*_E1*<br/>
這個區段範圍的下一個最重要的元件。

*_E2*<br/>
本節範圍中最重要的元件。

*_InputIterator*<br/>
輸入迭代器的類型。

*_Src*<br/>
To 要複製的物件。

*_Src_first*<br/>
來源容器中的開始反覆運算器。

*_Src_last*<br/>
來源容器中的結束反覆運算器。

*_Other*<br/>
其他資料來源。

*_Rank*<br/>
區段的順位。

*value_type*<br/>
複製之元素的資料類型。

## <a name="associated_accelerator_view"></a>associated_accelerator_view

取得在呼叫暫存函式以具現化 `array` 物件時，傳遞做為參數的第二個[accelerator_view](accelerator-view-class.md)物件。

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

將 `array` 的內容複寫到另一個 `array`。

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
要複製到其中的[array_view](array-view-class.md)物件。

## <a name="cpu_access_type"></a>cpu_access_type

取得此陣列允許的 CPU access_type。

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>data

傳回 `array`原始資料的指標。

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

陣列原始資料的指標。

## <a name="extent"></a>片區

取得[範圍](extent-class.md)物件，其定義 `array`的形狀。

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

傳回[accelerator_view](accelerator-view-class.md)物件，表示配置 `array` 物件的位置。 這個屬性只能在 CPU 上存取。

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>傳回值

`accelerator_view` 物件，表示配置 `array` 物件的位置。

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

取得在呼叫暫存函式以具現化 `array` 物件時，傳遞做為參數的第二個[accelerator_view](accelerator-view-class.md)物件。

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>傳回值

傳遞至預備函數的第二個[accelerator_view](accelerator-view-class.md)物件。

## <a name="get_cpu_access_type"></a>get_cpu_access_type

傳回此陣列允許的 CPU access_type。

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

## <a name="get_extent"></a>get_extent

傳回 `array`的[範圍](extent-class.md)物件。

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent` 的 `array` 物件。

## <a name="operator_vec"></a>運算子 std：： vector&lt;value_type&gt;

使用 `copy(*this, vector)`，將陣列隱含地轉換為 std：： vector 物件。

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>參數

*value_type*<br/>
向量元素的資料類型。

### <a name="return-value"></a>傳回值

`vector<T>` 類型的物件，其中包含陣列中包含的資料複本。

## <a name="operator_call"></a>operator （）

傳回參數所指定的元素值。

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
元素的位置。

*_I0*<br/>
這一節的最重要元件。

*_I1*<br/>
這個區段的下一個最重要的元件。

*_I2*<br/>
這一節的最重要元件。

*_I*<br/>
元素的位置。

### <a name="return-value"></a>傳回值

參數所指定的元素值。

## <a name="operator_at"></a>operator []

傳回位於指定索引處的元素。

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
索引。

*_I*<br/>
索引。

### <a name="return-value"></a>傳回值

位於指定索引處的元素。

## <a name="operator_eq"></a>operator =

複製指定之 `array` 物件的內容。

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源 `array` 物件。

*_Src*<br/>
要複製的來源 `array` 物件。

### <a name="return-value"></a>傳回值

這個 `array` 物件的參考。

## <a name="rank"></a>等級

儲存 `array`的排名。

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

透過一維 array_view 向量陣列，其選擇性的數值型別可能會與來源陣列不同。

### <a name="syntax"></a>語法

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Value_type2*<br/>
傳回之資料的資料類型。

### <a name="return-value"></a>傳回值

以陣列為基礎的 array_view 或 const array_view 物件，其中元素類型向量從 T 到 ElementType，而次序從 N 縮減為1。

### <a name="remarks"></a>備註

有時候，將多維陣列視為線性的一維陣列（可能具有與來源陣列不同的實數值型別），是很方便的方式。 您可以使用這個方法來達到此目的。
**注意**使用不同的數值型別來別的陣列物件是可能不安全的作業。 我們建議您小心使用此功能。

範例請見下列程式碼。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>截面

傳回位於指定之來源之 `array` 物件的子區段，並選擇性地傳回具有指定範圍的。

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
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

*value_type*<br/>
複製之元素的資料類型。

### <a name="return-value"></a>傳回值

傳回位於指定之來源之 `array` 物件的子區段，並選擇性地傳回具有指定範圍的。 只有在指定 `index` 物件時，子區段會包含關聯方格中的所有專案，這些專案的索引大於 `index` 物件中的元素索引。

## <a name="view_as"></a>view_as

將此陣列向量為不同次序的[array_view](array-view-class.md) 。

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_New_rank*<br/>
當做參數傳遞之 `extent` 物件的順位。

*_View_extent*<br/>
用來建立新[array_view](array-view-class.md)物件的範圍。

*value_type*<br/>
原始 `array` 物件和傳回的 `array_view` 物件中專案的資料類型。

### <a name="return-value"></a>傳回值

所結構化的[array_view](array-view-class.md)物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

---
title: array 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e0d0fde53cc7ffb885e8435fc82cbb899a3bc89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389529"
---
# <a name="array-class"></a>array 類別

表示用來將資料移至加速器的資料容器。

## <a name="syntax"></a>語法

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>參數

*value_type*<br/>
資料的項目型別。

*_Rank*<br/>
陣列陣序。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[陣列建構函式](#ctor)|初始化 `array` 類別的新執行個體。|
|[~ array 解構函式](#dtor)|終結`array`物件。|
### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[copy_to](#copy_to)|將陣列的內容複製到另一個陣列。|
|[data](#data)|傳回陣列的未經處理資料的指標。|
|[get_accelerator_view](#get_accelerator_view)|傳回[accelerator_view](accelerator-view-class.md)物件，代表陣列配置位置。 只能在 CPU 上，就可以存取這個屬性。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|取得第二個[accelerator_view](accelerator-view-class.md)預備的建構函式呼叫來具現化時，會將做為參數傳遞的物件`array`物件。|
|[get_cpu_access_type](#get_cpu_access_type)|傳回[access_type](concurrency-namespace-enums-amp.md#access_type)的陣列。 這個方法可以只在 CPU 上存取。|
|[get_extent](#get_extent)|傳回[範圍](extent-class.md)物件的陣列。|
|[reinterpret_as](#reinterpret_as)|傳回一維陣列，包含中的所有項目`array`物件。|
|[section](#section)|傳回的子區段`array`物件位於指定的來源，並選擇性地，具有指定的範圍。|
|[view_as](#view_as)|傳回[array_view](array-view-class.md)物件，建構自`array`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator std::vector&lt;value_type&gt;](#operator_vec)|會使用`copy(*this, vector)`來以隱含方式將陣列轉換成 std::[向量](../../../standard-library/vector-class.md)物件。|
|[operator()](#operator_call)|傳回參數所指定的項目值。|
|[operator[]](#operator_at)|傳回位於指定索引處的項目。|
|[operator=](#operator_eq)|將指定的內容複製`array`到這個物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|儲存陣列的陣序規範。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|取得[accelerator_view](accelerator-view-class.md)物件，代表陣列配置位置。 只能在 CPU 上，就可以存取這個屬性。|
|[associated_accelerator_view](#associated_accelerator_view)|取得第二個[accelerator_view](accelerator-view-class.md)預備的建構函式呼叫來具現化時，會將做為參數傳遞的物件`array`物件。|
|[cpu_access_type](#cpu_access_type)|取得[access_type](concurrency-namespace-enums-amp.md#access_type)表示 CPU 存取陣列的儲存體的方式。|
|[extent](#extent)|取得定義陣列圖形的範圍。|

## <a name="remarks"></a>備註

型別`array<T,N>`代表的密集且規則 （非不規則） *N*-位於特定位置，例如加速器或 CPU 的二維陣列。 陣列中元素的資料類型是`T`，必須與目標加速器相容的類型。 雖然陣序`N`，(的陣列以靜態方式判斷類型的一部分，陣列的範圍取決於執行階段，而且使用類別來表示`extent<N>`。

陣列可以有任意數目的維度，雖然有些功能專門用於`array`陣序為一、 二或三個物件。 如果您省略維度引數，預設值為 1。

陣列資料是連續配置在記憶體中。 最小顯著性維度中相差一的項目是在記憶體中相鄰的。

陣列在邏輯上視為數值類型，因為當陣列複製到另一個陣列，執行深層複製。 這兩個陣列永遠不會指向相同的資料。

`array<T,N>`類型會在幾個案例：

- 為資料容器，可用於在加速器上的計算。

- 為資料容器來保存在主機 CPU 上的記憶體 （也可以用來從其他陣列來回複製）。

- 為要做為主機至裝置複本中快速中繼的預備物件。

## <a name="inheritance-hierarchy"></a>繼承階層

`array`

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

##  <a name="dtor"></a> ~ 陣列

終結`array`物件。

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

取得[accelerator_view](accelerator-view-class.md)物件，代表陣列配置位置。 只能在 CPU 上，就可以存取這個屬性。

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> 陣列

初始化的新執行個體[array 類別](array-class.md)。 沒有任何預設建構函式`array<T,N>`。 所有建構函式只能在 CPU 上執行。 它們無法在 Direct3D 目標上執行。

```
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
指定陣列慣用的目標位置的 accelerator_view。

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md)物件，指定陣列的位置。

*_Cpu_access_type*<br/>
想要[access_type](concurrency-namespace-enums-amp.md#access_type) CPU 上的陣列。 此參數的預設值是`access_type_auto`離開 CPU`access_type`判斷執行階段。 實際 CPU`access_type`的陣列可以使用查詢`get_cpu_access_type`方法。

*_Extent*<br/>
在每個維度中陣列的範圍。

*_E0*<br/>
這個區段範圍的最重要的元件。

*_E1*<br/>
這個區段範圍的下一步 以-重要元件。

*_E2*<br/>
這個區段範圍的最不重要元件。

*_InputIterator*<br/>
輸入迭代器類型。

*_Src*<br/>
若要複製的物件。

*_Src_first*<br/>
來源容器中的開頭迭代器。

*_Src_last*<br/>
來源容器中結束迭代器。

*_Other*<br/>
其他資料來源。

*_Rank*<br/>
區段的順位。

*value_type*<br/>
複製的項目資料型別。

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

取得第二個[accelerator_view](accelerator-view-class.md)預備的建構函式呼叫來具現化時，會將做為參數傳遞的物件`array`物件。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

複製的內容`array`到另一個`array`。

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>參數

*_Dest*<br/>
[Array_view](array-view-class.md)複製到的物件。

##  <a name="cpu_access_type"></a> cpu_access_type

取得此陣列允許的 CPU access_type。

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> 資料

傳回的未經處理資料的指標`array`。

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>傳回值

陣列的未經處理資料指標。

##  <a name="extent"></a> 範圍

取得[程度](extent-class.md)定義的圖形物件`array`。

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view

傳回[accelerator_view](accelerator-view-class.md)物件，表示位置其中`array`配置的物件。 只能在 CPU 上，就可以存取這個屬性。

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>傳回值

`accelerator_view`物件所代表的位置，其中`array`配置的物件。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

取得第二個[accelerator_view](accelerator-view-class.md)預備的建構函式呼叫來具現化時，會將做為參數傳遞的物件`array`物件。

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>傳回值

第二個[accelerator_view](accelerator-view-class.md)物件傳遞至預備環境建構函式。

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

傳回此陣列允許的 CPU access_type。

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>傳回值

##  <a name="get_extent"></a> get_extent

傳回[程度](extent-class.md)物件的`array`。

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

`extent`物件的`array`。

##  <a name="operator_vec"></a> 運算子 std:: vector&lt;value_type&gt;

使用`copy(*this, vector)`來隱含地轉換成 std:: vector 物件的陣列。

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>參數

*value_type*<br/>
向量的元素資料型別。

### <a name="return-value"></a>傳回值

型別的物件`vector<T>`包含陣列中所包含的資料複本。

##  <a name="operator_call"></a> operator （)

傳回參數所指定的項目值。

```
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
項目的位置。

*_I0*<br/>
本節的原點的最重要的元件。

*_I1*<br/>
下一步-至-重要元件之原點的這一節。

*_I2*<br/>
本節中的來源最不重要元件。

*_I*<br/>
項目的位置。

### <a name="return-value"></a>傳回值

參數所指定項目值。

##  <a name="operator_at"></a> operator]

傳回位於指定索引處的項目。

```
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

位於指定索引處的項目。

##  <a name="operator_eq"></a> 運算子 =

將指定的內容複製`array`物件。

```
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`array`從複製的物件。

*_Src*<br/>
`array`從複製的物件。

### <a name="return-value"></a>傳回值

此參考`array`物件。

##  <a name="rank"></a> 陣序規範

儲存的陣序`array`。

```
static const int rank = _Rank;
```
## <a name="reinterpret_as"></a> reinterpret_as

轉換透過一維 array_view，或者可能有不同的實值型別，於來源陣列的陣列。

### <a name="syntax"></a>語法

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Value_type2*<br/>
傳回資料的資料型別。

### <a name="return-value"></a>傳回值

Array_view 或 const array_view 物件為基礎的陣列，陣從 T ElementType 並從 N 減少到 1 的陣序的項目類型。

### <a name="remarks"></a>備註

有時候很方便，好像是線性一維陣列，可能有不同的實值型別，於來源陣列檢視多維陣列。 若要這麼做，您可以使用這個方法。
**注意：** 重新解譯陣列物件，使用不同的實值型別是可能不安全的作業。 我們建議您謹慎使用這項功能。

下列程式碼提供一個範例。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> 區段

傳回的子區段`array`物件位於指定的來源，並選擇性地，具有指定的範圍。

```
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

*value_type*<br/>
複製的項目資料型別。

### <a name="return-value"></a>傳回值

傳回的子區段`array`物件位於指定的來源，並選擇性地，具有指定的範圍。 當只有`index`指定的物件，子區段會包含所有相關聯的方格中的元素，其大於中的項目索引的索引`index`物件。

##  <a name="view_as"></a> view_as

重新解譯此陣列做[array_view](array-view-class.md)為不同陣序。

```
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_New_rank*<br/>
陣序`extent`做為參數傳遞的物件。

*_View_extent*<br/>
用來建構新的範圍內[array_view](array-view-class.md)物件。

*value_type*<br/>
這兩個原始項目的資料型別`array`物件，並傳回`array_view`物件。

### <a name="return-value"></a>傳回值

[Array_view](array-view-class.md)建構的物件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

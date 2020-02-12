---
title: extent 類別 (C++ AMP)
ms.date: 03/27/2019
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
ms.openlocfilehash: 3e8dae7b76ea2efc852486a19f5d298cda477012
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126717"
---
# <a name="extent-class-c-amp"></a>extent 類別 (C++ AMP)

代表*n*個整數值的向量，指定具有原點為0之*N*維度空間的範圍。 向量中的值會從最重要到最低的順序排序。

## <a name="syntax"></a>語法

```cpp
template <int _Rank>
class extent;
```

### <a name="parameters"></a>參數

*_Rank*<br/>
`extent` 物件的順位。

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[範圍構造函式](#ctor)|初始化 `extent` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[contains](#contains)|確認指定的 `extent` 物件具有指定的次序。|
|[size](#size)|傳回範圍的線性大小總計（單位為專案）。|
|[圖示](#tile)|使用指定的維度所提供的磚範圍，產生 `tiled_extent` 物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator-](#operator_min)|傳回新的 `extent` 物件，它是藉由對應的 `extent` 元素減去 `index` 元素而建立的。|
|[operator--](#operator_min_min)|遞減 `extent` 物件的每個元素。|
|[operator%=](#operator_mod_eq)|當元素除以數位時，計算 `extent` 物件中每個元素的模數（餘數）。|
|[operator*=](#operator_star_eq)|將 `extent` 物件的每個元素乘以一個數位。|
|[operator/=](#operator_min_eq)|將 `extent` 物件的每個元素除以一個數位。|
|[範圍：： operator\[\]](#operator_at)|傳回位於指定之索引處的元素。|
|[operator+](#operator_add)|傳回新的 `extent` 物件，它是藉由加入對應的 `index` 和 `extent` 元素所建立。|
|[operator++](#operator_add_add)|遞增 `extent` 物件的每個元素。|
|[operator+=](#operator_add_eq)|將指定的數位加入至 `extent` 物件的每個元素。|
|[operator=](#operator_eq)|將另一個 `extent` 物件的內容複寫到其中。|
|[operator-=](#operator_min_eq)|從 `extent` 物件的每個元素減去指定的數位。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[次序常數](#rank_constant)|取得 `extent` 物件的順位。|

## <a name="inheritance-hierarchy"></a>繼承階層

`extent`

## <a name="contains"></a>包含

指出指定的[索引](index-class.md)值是否包含在 ' 範圍 ' 物件中。

### <a name="syntax"></a>語法

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
要測試的 `index` 值。

### <a name="return-value"></a>傳回值

如果指定的*索引*值包含在 `extent` 物件中，則**為 true** ;否則**為 false**。

## <a name="ctor"></a>片區

初始化 ' 範圍 ' 類別的新實例。

### <a name="syntax"></a>語法

```cpp
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Array*<br/>
`_Rank` 整數的陣列，用來建立新的 `extent` 物件。

*_I*<br/>
範圍的長度。

*_I0*<br/>
最重要維度的長度。

*_I1*<br/>
下一個最重要維度的長度。

*_I2*<br/>
最不重要維度的長度。

*_Other*<br/>
新 `extent` 物件所依據的 `extent` 物件。

## <a name="remarks"></a>備註

預設的函式會初始化等級為三的 `extent` 物件。

如果使用陣列來建立 `extent` 物件，陣列的長度必須符合 `extent` 物件的次序。

## <a name="operator_mod_eq"></a>運算子% =

當該元素除以數位時，計算 ' 範圍 ' 中每個專案的模數（餘數）。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要尋找其模數的數位。

### <a name="return-value"></a>傳回值

`extent` 物件。

## <a name="operator_star_eq"></a>運算子 * =

將 ' 範圍 ' 物件中的每個元素乘以指定的數目。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要相乘的數位。

### <a name="return-value"></a>傳回值

`extent` 物件。

## <a name="operator_add"></a>運算子 +

傳回藉由加入對應的 `index` 和 `extent` 元素所建立的新 `extent` 物件。

### <a name="syntax"></a>語法

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
`index` 物件，其中包含要加入的元素。

### <a name="return-value"></a>傳回值

新的 `extent` 物件。

## <a name="operator_add_add"></a>operator + +

遞增 ' 範圍 ' 物件的每個元素。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

若為前置運算子，則 `extent` 物件（`*this`）。 若為尾碼運算子，則為新的 `extent` 物件。

## <a name="operator_add_eq"></a>運算子 + =

將指定的數位加入至 ' 範圍 ' 物件的每個元素。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要加入的數位、索引或範圍。

### <a name="return-value"></a>傳回值

產生 `extent` 物件。

## <a name="operator_min"></a>操作

藉由從這個 `extent` 物件中的對應元素減去指定之 `index` 物件中的每個專案，建立新的 `extent` 物件。

### <a name="syntax"></a>語法

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
`index` 物件，其中包含要減去的元素。

### <a name="return-value"></a>傳回值

新的 `extent` 物件。

## <a name="operator_min_min"></a>operator--

遞減 ' 範圍 ' 物件中的每個元素。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

若為前置運算子，則 `extent` 物件（`*this`）。 若為尾碼運算子，則為新的 `extent` 物件。

## <a name="operator_div_eq"></a>operator/=

將 ' 範圍 ' 物件中的每個元素除以指定的數目。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要除以的數位。

### <a name="return-value"></a>傳回值

`extent` 物件。

## <a name="operator_min_eq"></a>operator-=

從 ' 範圍 ' 物件的每個元素減去指定的數位。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要減去的數位。

### <a name="return-value"></a>傳回值

產生 `extent` 物件。

## <a name="operator_eq"></a>operator =

將另一個 ' 範圍 ' 物件的內容複寫到這個。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的來源 `extent` 物件。

### <a name="return-value"></a>傳回值

這個 `extent` 物件的參考。

## <a name="operator_at"></a>範圍：： operator \[\]

傳回位於指定之索引處的元素。

### <a name="syntax"></a>語法

```cpp
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
從0到次序減1的整數。

### <a name="return-value"></a>傳回值

位於指定索引處的元素。

## <a name="rank_constant"></a>等級

儲存 ' 範圍 ' 物件的次序。

### <a name="syntax"></a>語法

```cpp
static const int rank = _Rank;
```

## <a name="size"></a>容量

傳回 `extent` 物件的線性大小總計（單位為元素）。

### <a name="syntax"></a>語法

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a>圖示

產生具有指定之圖格維度的 tiled_extent 物件。

```cpp
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```

### <a name="parameters"></a>參數

*_Dim0*<br/>
磚範圍中最重要的元件。
*_Dim1*<br/>
磚範圍的下一個最重要的元件。
*_Dim2*<br/>
磚範圍的最重要元件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

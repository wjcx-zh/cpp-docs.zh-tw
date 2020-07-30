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
ms.openlocfilehash: b9fd0ffb0c3ac6e0b80823e9f31c3615a045262b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222728"
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
物件的順位 `extent` 。

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[範圍構造函式](#ctor)|初始化 `extent` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[contains](#contains)|驗證指定的 `extent` 物件是否具有指定的次序。|
|[size](#size)|傳回範圍的線性大小總計（單位為專案）。|
|[磚](#tile)|產生 `tiled_extent` 物件，其中包含指定之維度所提供的磚範圍。|

### <a name="public-operators"></a>公用運算子

|Name|說明|
|----------|-----------------|
|[操作](#operator_min)|傳回新的 `extent` 物件，其建立方式是 `index` 從對應的元素減去元素 `extent` 。|
|[operator--](#operator_min_min)|遞減物件的每個元素 `extent` 。|
|[運算子% =](#operator_mod_eq)|當元素除以數位時，計算物件中每個元素的模數（餘數） `extent` 。|
|[運算子 * =](#operator_star_eq)|將物件的每個元素乘以 `extent` 一個數位。|
|[operator/=](#operator_min_eq)|將物件的每個元素除以 `extent` 一個數位。|
|[範圍：：運算子\[\]](#operator_at)|傳回位於指定之索引處的元素。|
|[運算子 +](#operator_add)|傳回新的 `extent` 物件，它是藉由加入對應的 `index` 和元素所建立 `extent` 。|
|[operator + +](#operator_add_add)|遞增物件的每個元素 `extent` 。|
|[運算子 + =](#operator_add_eq)|將指定的數位加入至物件的每個元素 `extent` 。|
|[operator =](#operator_eq)|將另一個物件的內容複寫 `extent` 到這個。|
|[operator-=](#operator_min_eq)|從物件的每個元素減去指定的數位 `extent` 。|

### <a name="public-constants"></a>公用常數

|Name|說明|
|----------|-----------------|
|[次序常數](#rank_constant)|取得物件的順位 `extent` 。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`extent`

## <a name="contains"></a><a name="contains"></a>包含

指出指定的[索引](index-class.md)值是否包含在 ' 範圍 ' 物件中。

### <a name="syntax"></a>語法

```cpp
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
要測試的 `index` 值。

### <a name="return-value"></a>傳回值

**`true`** 如果指定的*索引*值包含在物件中 `extent` ，則為，否則為 **`false`** 。

## <a name="extent"></a><a name="ctor"></a>片區

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
`_Rank`用來建立新物件的整數陣列 `extent` 。

*_I*<br/>
範圍的長度。

*_I0*<br/>
最重要維度的長度。

*_I1*<br/>
下一個最重要維度的長度。

*_I2*<br/>
最不重要維度的長度。

*_Other*<br/>
`extent`新 `extent` 物件所依據的物件。

## <a name="remarks"></a>備註

預設的函式 `extent` 會初始化等級為3的物件。

如果使用陣列來建立 `extent` 物件，陣列的長度必須符合物件的次序 `extent` 。

## <a name="operator"></a><a name="operator_mod_eq"></a>運算子% =

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

## <a name="operator"></a><a name="operator_star_eq"></a>運算子 * =

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

## <a name="operator"></a><a name="operator_add"></a>運算子 +

傳回新的 `extent` 物件，並藉由加入對應的 `index` 和元素來建立 `extent` 。

### <a name="syntax"></a>語法

```cpp
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
`index`包含要加入之元素的物件。

### <a name="return-value"></a>傳回值

新的 `extent` 物件。

## <a name="operator"></a><a name="operator_add_add"></a>operator + +

遞增 ' 範圍 ' 物件的每個元素。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

若為前置運算子，則為 `extent` 物件（ **`*this`** ）。 若為尾碼運算子，則為新的 `extent` 物件。

## <a name="operator"></a><a name="operator_add_eq"></a>運算子 + =

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

## <a name="operator-"></a><a name="operator_min"></a>操作

藉 `extent` 由 `index` 從這個物件中的對應元素減去指定物件中的每個專案，建立新的物件 `extent` 。

### <a name="syntax"></a>語法

```cpp
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
`index`物件，包含要減去的元素。

### <a name="return-value"></a>傳回值

新的 `extent` 物件。

## <a name="operator--"></a><a name="operator_min_min"></a>operator--

遞減 ' 範圍 ' 物件中的每個元素。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

若為前置運算子，則為 `extent` 物件（ **`*this`** ）。 若為尾碼運算子，則為新的 `extent` 物件。

## <a name="operator"></a><a name="operator_div_eq"></a>operator/=

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

## <a name="operator-"></a><a name="operator_min_eq"></a>operator-=

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

## <a name="operator"></a><a name="operator_eq"></a>operator =

將另一個 ' 範圍 ' 物件的內容複寫到這個。

### <a name="syntax"></a>語法

```cpp
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
`extent`要複製的物件。

### <a name="return-value"></a>傳回值

這個物件的參考 `extent` 。

## <a name="extentoperator-"></a><a name="operator_at"></a>範圍：：運算子\[\]

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

## <a name="rank"></a><a name="rank_constant"></a>等級

儲存 ' 範圍 ' 物件的次序。

### <a name="syntax"></a>語法

```cpp
static const int rank = _Rank;
```

## <a name="size"></a><a name="size"></a>容量

傳回物件的線性大小總計 `extent` （單位為元素）。

### <a name="syntax"></a>語法

```cpp
unsigned int size() const restrict(amp,cpu);
```

## <a name="tile"></a><a name="tile"></a>圖示

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

[Concurrency 命名空間（C++ AMP）](concurrency-namespace-cpp-amp.md)

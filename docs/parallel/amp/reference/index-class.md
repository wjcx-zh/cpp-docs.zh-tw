---
title: index 類別
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127799"
---
# <a name="index-class"></a>index 類別

定義*N*維度索引向量。

## <a name="syntax"></a>語法

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>參數

*_Rank*<br/>
順位或維度的數目。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[索引構造函式](#index_ctor)|初始化 `index` 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator--](#operator--)|遞減 `index` 物件的每個元素。|
|[operator%=](#operator_mod_eq)|當元素除以數位時，計算 `index` 物件中每個元素的模數（餘數）。|
|[operator*=](#operator_star_eq)|將 `index` 物件的每個元素乘以一個數位。|
|[operator/=](#operator_div_eq)|將 `index` 物件的每個元素除以一個數位。|
|[index：： operator\[\]](#operator_at)|傳回位於指定之索引處的元素。|
|[operator++](#operator_add_add)|遞增 `index` 物件的每個元素。|
|[operator+=](#operator_add_eq)|將指定的數位加入至 `index` 物件的每個元素。|
|[operator=](#operator_eq)|將指定 `index` 物件的內容複寫到這個。|
|[operator-=](#operator_-_eq)|從 `index` 物件的每個元素減去指定的數位。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[次序常數](#rank)|儲存 `index` 物件的順位。|

## <a name="inheritance-hierarchy"></a>繼承階層

`index`

## <a name="remarks"></a>備註

`index` 結構代表*n*個整數的座標向量，可指定在*N*維度空間中的唯一位置。 向量中的值會從最重要到最低的順序排序。 您可以使用[operator =](#operator_eq)來取得元件的值。

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="index_ctor"></a>索引構造函式

初始化索引類別的新實例。

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Array*<br/>
具有次序值的一維陣列。

*_I*<br/>
一維索引中的索引位置。

*_I0*<br/>
最重要維度的長度。

*_I1*<br/>
下一個最重要維度的長度。

*_I2*<br/>
最不重要維度的長度。

*_Other*<br/>
新索引物件所依據的索引物件。

## <a name="operator--"></a>operator--

遞減索引物件的每個元素。

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>傳回值

若為前置運算子，則為索引物件（* this）。 若為尾碼運算子，則為新的索引物件。

## <a name="operator_mod_eq"></a>運算子% =

當元素除以指定的數位時，計算索引物件中每個元素的模數（餘數）。

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要除以以尋找模數的數位。

## <a name="return-value"></a>傳回值

索引物件。

## <a name="operator_star_eq"></a>運算子 * =

將索引物件中的每個元素乘以指定的數目。

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要相乘的數位。

## <a name="operator_div_eq"></a>operator/=

將索引物件中的每個元素除以指定的數目。

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要除以的數位。

## <a name="operator_at"></a> operator\[\]

傳回位於指定位置之索引的元件。

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
從0到次序減1的整數。

### <a name="return-value"></a>傳回值

位於指定索引處的元素。

### <a name="remarks"></a>備註

下列範例會顯示索引的元件值。

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operator + +

遞增索引物件的每個元素。

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

若為前置運算子，則為索引物件（* this）。 若為尾碼運算子，則為新的索引物件。

## <a name="operator_add_eq"></a>運算子 + =

將指定的數位加入至索引物件的每個元素。

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要加入的數位。

### <a name="return-value"></a>傳回值

索引物件。

## <a name="operator_eq"></a>  operator=

將指定之索引物件的內容複寫到這個。

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要複製的目標索引物件。

### <a name="return-value"></a>傳回值

此索引物件的參考。

## <a name="operator_-_eq"></a>operator-=

從索引物件的每個元素減去指定的數位。

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要減去的數位。

### <a name="return-value"></a>傳回值

索引物件。

## <a name="rank"></a>等級

取得索引物件的順位。

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

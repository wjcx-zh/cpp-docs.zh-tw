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
ms.openlocfilehash: 50222015e6b365dc161fd4334067c26c7f288337
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365156"
---
# <a name="index-class"></a>index 類別

定義*N-* 維索引向量。

## <a name="syntax"></a>語法

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>參數

*_Rank*<br/>
排名或維度數。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[索引構函數](#index_ctor)|將 `index` 類別的新執行個體初始化。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[運算子--](#operator--)|聲明`index`物件的每個元素。|
|[運算子%*](#operator_mod_eq)|當該元素除以數位時,`index`計算物件中每個元素的模數(剩餘數)。|
|[運算子*](#operator_star_eq)|將`index`物件的每個元素乘以數位。|
|[操作員/*](#operator_div_eq)|將`index`物件的每個元素除以數位。|
|[索引::運算子\[\]](#operator_at)|返回指定索引處的元素。|
|[運算子*](#operator_add_add)|增加`index`物件的每個元素。|
|[運算子*](#operator_add_eq)|將指定的編號添加到`index`物件的每個元素。|
|[運算子*](#operator_eq)|將指定`index`物件的內容複製到此物件中。|
|[運算子-*](#operator_-_eq)|從`index`物件的每個元素中減去指定的數位。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[排名 常量](#rank)|存儲`index`物件的排名。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`index`

## <a name="remarks"></a>備註

該`index`結構表示*N*整數的座標向量,該向量指定*N-* 維空間中的唯一位置。 向量中的值從最顯著到最不顯著進行排序。 可以使用[運算符*](#operator_eq)檢索元件的值。

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="index-constructor"></a><a name="index_ctor"></a>索引構函數

初始化索引類的新實例。

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
具有排名值的一維陣組。

*_I*<br/>
一維索引中的索引位置。

*_I0*<br/>
最重要的維度的長度。

*_I1*<br/>
第二個最重要的維度的長度。

*_I2*<br/>
最小尺寸的長度。

*_Other*<br/>
新索引物件所基於的索引物件。

## <a name="operator--"></a><a name="operator--"></a>運算子--

聲明索引物件的每個元素。

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>傳回值

對於前置字元運算符,索引物件 (*THIS)。 對於後綴運算符,一個新的索引物件。

## <a name="operator"></a><a name="operator_mod_eq"></a>運算子%*

計算索引物件中每個元素的模數(剩餘數),將該元素除以指定數位。

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要除以查找模數的數位。

## <a name="return-value"></a>傳回值

索引物件。

## <a name="operator"></a><a name="operator_star_eq"></a>運算子*

將索引物件中的每個元素乘以指定數位。

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要乘法的數位。

## <a name="operator"></a><a name="operator_div_eq"></a>操作員/*

將索引物件中的每個元素除以指定數位。

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要除的編號。

## <a name="operator"></a><a name="operator_at"></a>算子\[\]

返回指定位置的索引的元件。

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
從 0 到排名減去 1 的整數。

### <a name="return-value"></a>傳回值

在指定索引處的元素。

### <a name="remarks"></a>備註

以下範例顯示索引的元件值。

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator"></a><a name="operator_add_add"></a>運算子*

增加索引物件的每個元素。

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>傳回值

對於前置字元運算符,索引物件 (*THIS)。 對於後綴運算符,一個新的索引物件。

## <a name="operator"></a><a name="operator_add_eq"></a>運算子*

將指定的編號添加到索引物件的每個元素。

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
要添加的編號。

### <a name="return-value"></a>傳回值

索引物件。

## <a name="operator"></a><a name="operator_eq"></a>運算子*

將指定索引物件的內容複製到此物件中。

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Other*<br/>
要從中複製的索引物件。

### <a name="return-value"></a>傳回值

對此索引物件的引用。

## <a name="operator-"></a><a name="operator_-_eq"></a>運算子-*

從索引物件的每個元素中減去指定的數位。

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

## <a name="rank"></a><a name="rank"></a>排名

獲取索引物件的排名。

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>另請參閱

[併發命名空間(C++ AMP)](concurrency-namespace-cpp-amp.md)

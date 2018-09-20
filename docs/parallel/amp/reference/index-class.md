---
title: index 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 154f9b4835f7dc18fcf45de53b078d3d5b649e37
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446917"
---
# <a name="index-class"></a>index 類別

定義*N*-維度的索引 pographics cpp amp.md。

## <a name="syntax"></a>語法

```
template <int _Rank>
class index;
```

#### <a name="parameters"></a>參數

*_Rank*<br/>
陣序規範或維度數目。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[索引建構函式](#ctor)|初始化 `index` 類別的新執行個體。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator--](#operator--)|遞減的每個項目`index`物件。|
|[operator(mod)=](#operator_mod_eq)|計算模數 （餘數） 中的每個項目的`index`物件時，項目除以某個數字。|
|[operator*=](#operator_star_eq)|每個元素乘`index`數字的物件。|
|[operator/=](#operator_div_eq)|每個項目除以`index`數字的物件。|
|[index::operator\[\]](#operator_at)|傳回位於指定索引處的項目。|
|[operator++](#operator_add_add)|遞增的每個項目`index`物件。|
|[operator+=](#operator_add_eq)|將指定的數目的每個項目加入`index`物件。|
|[operator=](#operator_eq)|將指定的內容複製`index`到這個物件。|
|[operator-=](#operator_-_eq)|減去指定的每個元素的數值`index`物件。|

### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|儲存的陣序`index`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`index`

## <a name="remarks"></a>備註

`index`結構表示的座標向量*N*指定一個唯一的位置中的整數*N*-維度的空間。 向量中的值排序從最大顯著性到最不重要。 您可以擷取使用元件的值[運算子 =](#operator_eq)。

## <a name="requirements"></a>需求

**標頭︰** amp.h

**命名空間：** 並行

## <a name="index_ctor"></a> 索引建構函式

初始化索引類別的新執行個體。

```
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
陣序值的一維陣列。

*_I*<br/>
中的索引位置的一維索引。

*_I0*<br/>
最高有效維度的長度。

*_I1*<br/>
下一步-至-最高有效維度的長度。

*_I2*<br/>
最小顯著性維度的長度。

*_Other*<br/>
新的索引物件所依據的索引物件。

## <a name="operator--"></a>  operator-

遞減索引物件的每個項目。
```
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```
### <a name="return-values"></a>傳回值

為前置運算子，index 物件 (* 這)。 為後置運算子，新的索引物件。

## <a name="operator_mod_eq"></a>  operator(mod) =

項目除以指定數字時，會計算的每個項目中的索引物件的模數 （餘數）。

```
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```
### <a name="parameters"></a>參數

*_Rhs*<br/>
若要尋找的模數由除的數字。

## <a name="return-value"></a>傳回值
Index 物件。

## <a name="operator_star_eq"></a>  operator*=

乘以指定的數值索引物件中每個項目。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Rhs*<br/>
要相乘的數字。

## <a name="operator_div_eq"></a>  operator / =

索引物件中的每個項目除以指定數字。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>參數

*_Rhs*<br/>
要除以的數字。

## <a name="operator_at"></a> operator\[\]

傳回指定位置處的索引元件。

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數

*_Index*<br/>
從 0 到順位減 1 的整數。

### <a name="return-value"></a>傳回值

位於指定索引處的項目。

### <a name="remarks"></a>備註

下列範例會顯示元件值的索引。
```
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator++

遞增的索引物件的每個項目。
```
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```
### <a name="return-value"></a>傳回值

為前置運算子，index 物件 (* 這)。 為後置運算子，新的索引物件。

## <a name="operator_add_eq"></a>  operator+=

將指定的數目的索引物件的每個項目。
```
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>參數

*_Rhs*<br/>
要加入的數字。

### <a name="return-value"></a>傳回值

Index 物件。

## <a name="operator_eq"></a>  operator=

將指定的索引物件的內容複製到這一個。
```
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```
### <a name="parameters"></a>參數

*_Other*<br/>
要複製的索引物件。

### <a name="return-value"></a>傳回值

此索引物件的參考。

## <a name="operator_-_eq"></a>  運算子 =

減去指定的數值索引物件的每個項目。
```
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```
### <a name="parameters"></a>參數

*_Rhs*<br/>
要減去的數字。

### <a name="return-value"></a>傳回值

Index 物件。

## <a name="rank"></a>  陣序規範
  取得 index 物件的陣序規範。
```
static const int rank = _Rank;
```
## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

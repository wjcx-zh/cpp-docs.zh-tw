---
title: extent 類別 (c + + AMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- extent
- AMP/extent
- AMP/Concurrency::extent::extent
- AMP/Concurrency::extent::contains
- AMP/Concurrency::extent::size
- AMP/Concurrency::extent::tile
- AMP/Concurrency::extent::rank Constant
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 59600343a06a2c3c0d4f5b55efadaa09c43452d9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067697"
---
# <a name="extent-class-c-amp"></a>extent 類別 (C++ AMP)
代表向量的位元*N*整數值，指定的界限*N*-維空間的 0 為原點。 向量中的值排序從最大顯著性到最不重要。

### <a name="syntax"></a>語法

```  
template <int _Rank>
class extent;
```  

### <a name="parameters"></a>參數
*_Rank*<br/>
陣序`extent`物件。

## <a name="requirements"></a>需求
**標頭︰** amp.h

**命名空間：** 並行

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[範圍建構函式](#ctor)|初始化 `extent` 類別的新執行個體。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[包含](#contains)|確認指定`extent`物件具有指定的陣序。|
|[size](#size)|傳回範圍 （以單位的項目） 的總線性大小。|
|[tile](#tile)|會產生`tiled_extent`指定維度的所指定的 tile 的物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[operator-](#operator_min)|傳回新`extent`物件，由減去`index`從相對應的項目`extent`項目。|
|[operator--](#operator_min_min)|遞減的每個項目`extent`物件。|
|[operator%=](#operator_mod_eq)|計算模數 （餘數） 中的每個項目的`extent`物件時，項目除以某個數字。|
|[operator*=](#operator_star_eq)|每個元素乘`extent`數字的物件。|
|[operator/=](#operator_min_eq)|每個項目除以`extent`數字的物件。|
|[extent::operator\[\]](#operator_at)|傳回位於指定索引處的項目。|
|[operator+](#operator_add)|傳回新`extent`由加入對應的物件`index`和`extent`項目。|
|[operator++](#operator_add_add)|遞增的每個項目`extent`物件。|
|[operator+=](#operator_add_eq)|將指定的數目的每個項目加入`extent`物件。|
|[operator=](#operator_eq)|複製的另一個內容`extent`到這個物件。|
|[operator-=](#operator_min_eq)|減去指定的每個元素的數值`extent`物件。|


### <a name="public-constants"></a>公用常數

|名稱|描述|
|----------|-----------------|
|[rank 常數](#rank)|取得的順位`extent`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層
`extent`  


## <a name="contains"></a> 包含

指出是否指定[index](index-class.md) '範圍' 物件中包含值。

### <a name="syntax"></a>語法

```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Index*<br/>
`index`若要測試的值。

### <a name="return-value"></a>傳回值
`true` 如果指定`index`值包含於`extent`物件; 否則`false`。

##  <a name="ctor"></a> 範圍

初始化 '範圍' 類別的新執行個體。

### <a name="syntax"></a>語法

```  
extent() restrict(amp,cpu);
extent(const extent<_Rank>& _Other) restrict(amp,cpu);
explicit extent(int _I) restrict(amp,cpu);
extent(int _I0,  int _I1) restrict(amp,cpu);
extent(int _I0,  int _I1, int _I2) restrict(amp,cpu);
explicit extent(const int _Array[_Rank])restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Array*<br/>
陣列`_Rank`用來建立新的整數`extent`物件。

*_I*<br/>
範圍的長度。

*_I0*<br/>
最高有效維度的長度。

*_I1*<br/>
下一步-至-最高有效維度的長度。

*_I2*<br/>
最小顯著性維度的長度。

*_Other*<br/>
`extent`物件上的新`extent`物件為基礎。

## <a name="remarks"></a>備註
無參數建構函式初始化`extent`具有三個等級的物件。

如果陣列用來建構`extent`物件陣列的長度必須符合的陣序`extent`物件。

##  <a name="operator_mod_eq"></a> operator %=

當項目除以某個數字時，會計算 '範圍' 中的每個元素的模數 （餘數）。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
要尋找的模數的數字。

### <a name="return-value"></a>傳回值
`extent` 物件。

##  <a name="operator_star_eq"></a> 運算子 * =

乘以指定的數值 '範圍' 物件中每個項目。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
要相乘的數字。

### <a name="return-value"></a>傳回值
`extent` 物件。

## <a name="operator_add"></a> operator +

傳回新`extent`藉由新增對應所建立的物件`index`和`extent`項目。

### <a name="syntax"></a>語法

```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
`index`物件，其中包含要加入的元素。

### <a name="return-value"></a>傳回值
新的 `extent` 物件。

##  <a name="operator_add_add"></a> operator + +

遞增 '範圍' 物件的每個項目。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator++() restrict(amp,cpu);
extent<_Rank> operator++(int)restrict(amp,cpu);
```  

### <a name="return-value"></a>傳回值
前置運算子，如`extent`物件 (`*this`)。 為後置運算子中，新`extent`物件。

##  <a name="operator_add_eq"></a> operator + =

將 '範圍' 物件的每個項目中指定的數目。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
數字、 索引或範圍加入。

### <a name="return-value"></a>傳回值
產生 `extent` 物件。

##  <a name="operator_min"></a> 運算子-

建立新`extent`物件中指定的每個元素減去`index`物件中的對應項目`extent`物件。

### <a name="syntax"></a>語法

```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
`index`物件，其中包含要減去的項目。

### <a name="return-value"></a>傳回值
新的 `extent` 物件。

##  <a name="operator_min_min"></a> operator-

遞減 '範圍' 物件中的每個項目。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator--() restrict(amp,cpu);
extent<_Rank> operator--(int)restrict(amp,cpu);
```  

### <a name="return-value"></a>傳回值
前置運算子，如`extent`物件 (`*this`)。 為後置運算子中，新`extent`物件。

##  <a name="operator_div_eq"></a> operator / =

'範圍' 物件中的每個項目除以指定數字。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
要除以的數字。

### <a name="return-value"></a>傳回值
`extent` 物件。

##  <a name="operator_min_eq"></a> 運算子 =

減去 '範圍' 物件的每個項目指定的數值。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Rhs*<br/>
要減去的數字。

### <a name="return-value"></a>傳回值
產生 `extent` 物件。

##  <a name="operator_eq"></a> 運算子 =

另一個 '範圍' 物件的內容複製到這一個。

### <a name="syntax"></a>語法

```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Other*<br/>
`extent`從複製的物件。

### <a name="return-value"></a>傳回值
此參考`extent`物件。

##  <a name="operator_at"></a> extent:: operator \[\]
傳回位於指定索引處的項目。

### <a name="syntax"></a>語法

```  
int operator[](unsigned int _Index) const restrict(amp,cpu);
int& operator[](unsigned int _Index) restrict(amp,cpu);
```  

### <a name="parameters"></a>參數
*_Index*<br/>
從 0 到順位減 1 的整數。

### <a name="return-value"></a>傳回值
位於指定索引處的項目。

##  <a name="rank_constant"></a> 陣序規範

儲存 '範圍' 物件的陣序。

### <a name="syntax"></a>語法

```  
static const int rank = _Rank;
```  

##  <a name="size"></a> 大小

傳回總線性大小`extent`（以單位的項目） 的物件。

### <a name="syntax"></a>語法

```  
unsigned int size() const restrict(amp,cpu);
```  

## <a name="tile"></a> 圖格

會產生與指定的 tile 維度 tiled_extent 物件。

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>參數
*_Dim0*<br/>
並排範圍的最重要的元件。
*_Dim1*<br/>
並排範圍的下一步 以-重要元件。
*_Dim2*<br/>
並排範圍的最小顯著性的元件。

## <a name="see-also"></a>另請參閱

[Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

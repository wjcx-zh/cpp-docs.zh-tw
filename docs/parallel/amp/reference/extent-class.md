---
title: "extent 類別 (c + + AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a8606b01ac5d3676b06c93c373677f2eb85d954
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="extent-class-c-amp"></a>extent 類別 (C++ AMP)
代表向量*N*整數值，指定的界限*N*-維度具有 0 的原點的空間。 在向量中的值為從最大顯著性到最小顯著性排序。  
  
### <a name="syntax"></a>語法  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
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
|[contains](#contains)|確認指定`extent`物件具有指定的陣序規範。|  
|[size](#size)|傳回線性的大小總計 （以元素為單位） 的範圍。|  
|[tile](#tile)|會產生`tiled_extent`指定維度與所指定的圖格範圍的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator-](#operator_min)|傳回新`extent`物件所建立的減去`index`從對應的項目`extent`項目。|  
|[operator--](#operator_min_min)|遞減的每個項目`extent`物件。|  
|[operator%=](#operator_mod_eq)|計算每個項目中的模數 （餘數）`extent`物件時數字除以該元素。|  
|[operator*=](#operator_star_eq)|乘以每個項目`extent`物件數目。|  
|[operator/=](#operator_min_eq)|將分割的每個項目`extent`物件數目。|  
|[extent::operator\[\]](#operator_at)|傳回指定索引處的項目。|  
|[operator+](#operator_add)|傳回新`extent`由加入對應的物件`index`和`extent`項目。|  
|[operator++](#operator_add_add)|遞增的每個項目`extent`物件。|  
|[operator+=](#operator_add_eq)|將指定的數目的每個項目加入`extent`物件。|  
|[operator=](#operator_eq)|複製的另一個內容`extent`成這一個物件。|  
|[operator-=](#operator_min_eq)|從每個項目指定的數目減掉`extent`物件。|  

  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[rank 常數](#rank)|取得的順位`extent`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `extent`  


## <a name="contains"></a> 包含 

指出是否指定[索引](index-class.md)'範圍' 物件中包含值。  
  
### <a name="syntax"></a>語法  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 `index`来測試值。  
  
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
 `_Array`  
 陣列`_Rank`用來建立新的整數`extent`物件。  
  
 `_I`  
 範圍的長度。  
  
 `_I0`  
 最重要的維度的長度。  
  
 `_I1`  
 下一步-到-最高有效維度的長度。  
  
 `_I2`  
 最小顯著性維度的長度。  
  
 `_Other`  
 `extent`物件上的新`extent`物件為基礎。  
  
## <a name="remarks"></a>備註  
 無參數建構函式初始化`extent`具有三個等級的物件。  
  
 如果陣列用來建構`extent`物件陣列的長度必須符合的陣序`extent`物件。  
  
##  <a name="operator_mod_eq"></a> operator%= 

數字除以該元素時，計算每個項目的 '範圍' 中的模數 （餘數）。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 要尋找的模數的數字。  
  
### <a name="return-value"></a>傳回值  
 `extent` 物件。  
  
##  <a name="operator_star_eq"></a> operator*= 

乘上每個項目中指定數目的 '範圍' 物件。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 要相乘的數字。  
  
### <a name="return-value"></a>傳回值  
 `extent` 物件。  
  
## <a name="operator_add"></a> operator + 

傳回新`extent`物件藉由新增對應建立`index`和`extent`項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank> operator+(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 `index`物件，其中包含要加入項目。  
  
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
 前置運算子，如`extent`物件 (`*this`)。 若為後置運算子，新`extent`物件。  
  
##  <a name="operator_add_eq"></a> operator+= 

將指定的數字加入至 '範圍' 物件的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator+=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator+=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 號碼、 索引或範圍加入。  
  
### <a name="return-value"></a>傳回值  
 產生 `extent` 物件。  
  
##  <a name="operator_min"></a> operator- 

建立新`extent`物件所指定的每個元素減去`index`從對應的項目，這個物件`extent`物件。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 `index`物件，其中包含要減去的項目。  
  
### <a name="return-value"></a>傳回值  
 新的 `extent` 物件。  
  
##  <a name="operator_min_min"></a> --運算子 

遞減 '範圍' 物件中的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>傳回值  
 前置運算子，如`extent`物件 (`*this`)。 若為後置運算子，新`extent`物件。  
  
##  <a name="operator_div_eq"></a> operator / = 

指定的數字除以 '範圍' 物件中的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator/=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 要除以的數字。  
  
### <a name="return-value"></a>傳回值  
 `extent` 物件。  
  
##  <a name="operator_min_eq"></a> 運算子 = 

指定從數目減掉 '範圍' 物件的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator-=(const extent<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(const index<_Rank>& _Rhs) restrict(amp,cpu);    
extent<_Rank>& operator-=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 要減去的數字。  
  
### <a name="return-value"></a>傳回值  
 產生 `extent` 物件。  
  
##  <a name="operator_eq"></a> 運算子 = 

另一個 '範圍' 物件的內容複製到這裡。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `extent`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 此參考`extent`物件。  
  
##  <a name="operator_at"></a> extent:: operator \[\] 
傳回指定索引處的項目。  
  
### <a name="syntax"></a>語法  
  
```  
int operator[](unsigned int _Index) const restrict(amp,cpu);    
int& operator[](unsigned int _Index) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 從 0 到陣序規範減 1 的整數。  
  
### <a name="return-value"></a>傳回值  
 所指定索引處的項目。  
  
##  <a name="rank_constant"></a> 順位 

儲存 '範圍' 物件的排列次序。  
  
### <a name="syntax"></a>語法  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="size"></a> 大小 

傳回的線性大小總計`extent`物件 （以元素為單位）。  
  
### <a name="syntax"></a>語法  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="tile"></a> 圖格 

產生具有指定的並排顯示維度 tiled_extent 物件。

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>參數
`_Dim0` 並排顯示範圍的最重要的元件。
`_Dim1` 並排顯示範圍的下一步-到-最高有效的元件。
`_Dim2` 並排顯示範圍的最不重要的元件。


  
## <a name="see-also"></a>請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

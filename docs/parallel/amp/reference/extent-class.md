---
title: "extent 類別 (c + + AMP) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::extent
dev_langs:
- C++
helpviewer_keywords:
- extent structure
ms.assetid: edb5de3d-3935-4dbb-8365-4cc6c4fb0269
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 8aa89b882ed075a8cdf0166d43fde1a5bfe7683d
ms.lasthandoff: 02/24/2017

---
# <a name="extent-class-c-amp"></a>extent 類別 (C++ AMP)
代表向量*N*整數值，指定的界限*N*-維度具有 0 原點的空間。 在向量中的值為從最大顯著性到最小顯著性排序。  
  
### <a name="syntax"></a>語法  
  
```  
template <int _Rank>  
class extent;  
```  
  
### <a name="parameters"></a>參數  
 `_Rank`  
 陣序規範`extent`物件。  

 ## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[範圍建構函式](#ctor)|初始化 `extent` 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[包含方法](#contains)|確認指定`extent`物件具有指定之陣序。|  
|[size 方法](#size)|傳回線性的大小總計 （以單位的項目） 的程度。|  
|[並排顯示方法](#tile)|會產生`tiled_extent`指定維度與所指定的區塊範圍的物件。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[operator-運算子](#operator_min)|傳回新`extent`物件所建立的減去`index`自對應的項目`extent`項目。|  
|[運算子-運算子](#operator_min_min)|遞減的每個項目`extent`物件。|  
|[operator %= 運算子](#operator_mod_eq)|計算每個項目中的模數 （餘數）`extent`數字除以該元素的物件。|  
|[運算子 * = 運算子](#operator_star_eq)|將每個項目`extent`物件數。|  
|[運算子 / = 運算子](#operator_min_eq)|會將每個項目`extent`物件數。|  
|[extent:: operator\[\]](#operator_at)|傳回指定索引處的項目。|  
|[operator + 運算子](#operator_add)|傳回新`extent`由加入對應的物件`index`和`extent`項目。|  
|[operator + + 運算子](#operator_add_add)|遞增的每個項目`extent`物件。|  
|[運算子 + = 運算子](#operator_add_eq)|將指定的數目的每個項目加入`extent`物件。|  
|[運算子 = 運算子](#operator_eq)|複製的另一個內容`extent`到這裡的物件。|  
|[operator-= 運算子](#operator_min_eq)|從各個項目指定的數目減掉`extent`物件。|  

  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[rank 常數](#rank)|取得的順位`extent`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `extent`  


## <a name="a-namecontainsa-contains"></a><a name="contains"></a>包含 

指出是否指定[索引](index-class.md)'範圍' 物件中包含值。  
  
### <a name="syntax"></a>語法  
  
```  
bool contains(const index<rank>& _Index) const restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Index`  
 `index`来測試值。  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定`index`值包含於`extent`物件; 否則`false`。  
  
##  <a name="a-namectora-extent"></a><a name="ctor"></a>範圍 

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
 下一步-至-最大顯著性維度的長度。  
  
 `_I2`  
 最小顯著性的維度的長度。  
  
 `_Other`  
 `extent`物件上的新`extent`物件為基礎。  
  
## <a name="remarks"></a>備註  
 無參數建構函式初始化`extent`具有三個等級的物件。  
  
 如果陣列用來建構`extent`物件陣列的長度必須符合的陣序規範`extent`物件。  
  
##  <a name="a-nameoperatormodeqa-operator"></a><a name="operator_mod_eq"></a>operator %= 

數字除以該元素時，計算每個項目與 「 範圍 」 中的模數 （餘數）。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator%=(int _Rhs) restrict(cpu, direct3d);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 若要尋找的模數數目。  
  
### <a name="return-value"></a>傳回值  
 `extent` 物件。  
  
##  <a name="a-nameoperatorstareqa-operator"></a><a name="operator_star_eq"></a>運算子 * = 

將指定數目的 '範圍' 物件中的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator*=(int _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 要相乘的數字。  
  
### <a name="return-value"></a>傳回值  
 `extent` 物件。  
  
## <a name="a-nameoperatoradda-operator"></a><a name="operator_add"></a>運算子 + 

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
  
##  <a name="a-nameoperatoraddadda-operator"></a><a name="operator_add_add"></a>operator + + 

遞增 '範圍' 物件的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator++() restrict(amp,cpu);    
extent<_Rank> operator++(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>傳回值  
 前置運算子，如`extent`物件 (`*this`)。 後置運算子，新`extent`物件。  
  
##  <a name="a-nameoperatoraddeqa-operator"></a><a name="operator_add_eq"></a>operator + = 

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
  
##  <a name="a-nameoperatormina-operator-"></a><a name="operator_min"></a>operator- 

建立新`extent`物件減去指定的每個項目`index`從對應的項目，在此物件`extent`物件。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank> operator-(const index<_Rank>& _Rhs) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
 `index`物件，其中包含要減去的項目。  
  
### <a name="return-value"></a>傳回值  
 新的 `extent` 物件。  
  
##  <a name="a-nameoperatorminmina-operator--"></a><a name="operator_min_min"></a>運算子- 

遞減 '範圍' 物件中的每個項目。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator--() restrict(amp,cpu);    
extent<_Rank> operator--(int)restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>傳回值  
 前置運算子，如`extent`物件 (`*this`)。 後置運算子，新`extent`物件。  
  
##  <a name="a-nameoperatordiveqa-operator"></a><a name="operator_div_eq"></a>運算子 / = 

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
  
##  <a name="a-nameoperatormineqa-operator-"></a><a name="operator_min_eq"></a>運算子 = 

減去 '範圍' 物件的每個項目從指定的數目。  
  
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
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

另一個 '範圍' 物件的內容複製到這裡。  
  
### <a name="syntax"></a>語法  
  
```  
extent<_Rank>& operator=(const extent<_Rank>& _Other) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>參數  
 `_Other`  
 `extent`從複製的物件。  
  
### <a name="return-value"></a>傳回值  
 參考`extent`物件。  
  
##  <a name="a-nameoperatorata-extentoperator-"></a><a name="operator_at"></a>extent:: operator\[\] 
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
  
##  <a name="a-namerankconstanta-rank"></a><a name="rank_constant"></a>陣序規範 

儲存 '範圍' 物件的順位。  
  
### <a name="syntax"></a>語法  
  
```  
static const int rank = _Rank;  
```  
  
##  <a name="a-namesizea-size"></a><a name="size"></a>大小 

傳回線性的大小總計`extent`（單位的項目） 的物件。  
  
### <a name="syntax"></a>語法  

```  
unsigned int size() const restrict(amp,cpu);  
```  
  
## <a name="a-nametilea-tile"></a><a name="tile"></a>並排顯示 

會產生具有指定的並排顯示維度的 tiled_extent 物件。

```
template <int _Dim0>
tiled_extent<_Dim0> tile() const ;

template <int _Dim0, int _Dim1>
tiled_extent<_Dim0, _Dim1> tile() const ;

template <int _Dim0, int _Dim1, int _Dim2>
tiled_extent<_Dim0, _Dim1, _Dim2> tile() const ;
```  
### <a name="parameters"></a>參數
`_Dim0`並排顯示範圍的最重要的元件。
`_Dim1`磚狀下一步-至-最大顯著性的元件。
`_Dim2`並排顯示範圍的最小顯著性的元件。


  
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (c + + AMP)](concurrency-namespace-cpp-amp.md)


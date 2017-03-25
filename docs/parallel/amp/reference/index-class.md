---
title: "index 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
dev_langs:
- C++
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
caps.latest.revision: 20
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 52c19da3cb8de10c3963ca3b795cac1babb3dc7a
ms.lasthandoff: 03/17/2017

---
# <a name="index-class"></a>index 類別
定義*N*-維度的索引 pographics cpp amp.md。  
  
## <a name="syntax"></a>語法  
  
```  
template <int _Rank>  
class index;  
```  
  
#### <a name="parameters"></a>參數  
 `_Rank`  
 陣序規範或維度數目。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[索引建構函式](#ctor)|初始化 `index` 類別的新執行個體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator--](#operator--)|遞減的每個項目`index`物件。|  
|[operator(mod) =](#operator_mod_eq)|計算每個項目中的模數 （餘數）`index`數字除以該元素的物件。|  
|[operator*=](#operator_star_eq)|將每個項目`index`物件數。|  
|[operator/=](#operator_div_eq)|會將每個項目`index`物件數。|  
|[index:: operator\[\]](#operator_at)|傳回指定索引處的項目。|  
|[operator++](#operator_add_add)|遞增的每個項目`index`物件。|  
|[operator+=](#operator_add_eq)|將指定的數目的每個項目加入`index`物件。|  
|[operator=](#operator_eq)|將指定的內容複製`index`到這裡的物件。|  
|[operator-=](#operator_-_eq)|從各個項目指定的數目減掉`index`物件。|  

  
### <a name="public-constants"></a>公用常數  
  
|名稱|說明|  
|----------|-----------------|  
|[rank 常數](#rank)|儲存的陣序規範`index`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `index`  
  
## <a name="remarks"></a>備註  
 `index`結構代表座標的向量*N*指定中的唯一位置的整數*N*-維度空間。 在向量中的值為從最大顯著性到最小顯著性排序。 您可以擷取使用元件的值[運算子 =](#operator_eq)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** amp.h  
  
 **命名空間：** 並行  


## <a name="index_ctor"></a>索引建構函式
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

_Array  
等級值的一維陣列。  
（_I)  
中的一維索引的索引位置。  
_I0  
最重要的維度的長度。  
_I1  
下一步-至-最大顯著性維度的長度。  
_I2  
最小顯著性的維度的長度。  
_Other  
新的索引物件所依據的索引物件。  

## <a name="operator--"></a>運算子-
遞減索引物件的每個項目。  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>傳回值
前置運算子，而索引物件的 (* 這)。 後置運算子，新的索引物件。

## <a name="operator_mod_eq"></a>operator(mod) =   
該項目除以指定的數目時，會計算每個項目中的索引物件的模數 （餘數）。

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>參數
_Rhs 模數藉由將數字。
傳回值的索引物件。

## <a name="operator_star_eq"></a>運算子 * =   
乘上每個項目中指定數目的索引物件。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數
_Rhs 要相乘的數字。

## <a name="operator_div_eq"></a>運算子 / = 
指定數字除以索引物件中的每個項目。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>參數
_Rhs 要除以的數字。

## <a name="operator_at"></a>  operator\[\]  
傳回元件的指定位置處的索引。

```
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數
_Index 從 0 到陣序規範減 1 的整數。

### <a name="return-value"></a>傳回值
所指定索引處的項目。

### <a name="remarks"></a>備註
下列範例會顯示元件值的索引。
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>operator + +   
遞增索引物件的每個項目。
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>傳回值
前置運算子，而索引物件的 (* 這)。 後置運算子，新的索引物件。

## <a name="operator_add_eq"></a>operator + =   
將指定的數字加入至索引物件的每個項目。
```  
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>參數
_Rhs 要新增的數字。

### <a name="return-value"></a>傳回值
索引物件。

## <a name="operator_eq"></a>  operator=   
將指定的索引物件的內容複製到這裡。
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>參數
_Other 從複製的索引物件。

### <a name="return-value"></a>傳回值
此索引物件的參考。

## <a name="operator_-_eq"></a>運算子 =
減去 index 物件的每個項目從指定的數目。
```  
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```  
### <a name="parameters"></a>參數
_Rhs 要減去的數字。

### <a name="return-value"></a>傳回值
索引物件。   

## <a name="rank"></a>陣序規範  
  取得索引物件的順位。
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)


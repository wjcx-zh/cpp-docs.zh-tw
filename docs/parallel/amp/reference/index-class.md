---
title: index 類別 |Microsoft 文件
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
ms.openlocfilehash: 594ee94bbbfc19bc6fcceb9ae7f0760d9ec877dc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695333"
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
 陣序或維度數目。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[索引建構函式](#ctor)|初始化 `index` 類別的新執行個體。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[operator--](#operator--)|遞減的每個項目`index`物件。|  
|[operator(mod)=](#operator_mod_eq)|計算每個項目中的模數 （餘數）`index`物件時數字除以該元素。|  
|[operator*=](#operator_star_eq)|乘以每個項目`index`物件數目。|  
|[operator/=](#operator_div_eq)|將分割的每個項目`index`物件數目。|  
|[index::operator\[\]](#operator_at)|傳回指定索引處的項目。|  
|[operator++](#operator_add_add)|遞增的每個項目`index`物件。|  
|[operator+=](#operator_add_eq)|將指定的數目的每個項目加入`index`物件。|  
|[operator=](#operator_eq)|將指定的內容複製`index`成這一個物件。|  
|[operator-=](#operator_-_eq)|從每個項目指定的數目減掉`index`物件。|  

  
### <a name="public-constants"></a>公用常數  
  
|名稱|描述|  
|----------|-----------------|  
|[rank 常數](#rank)|儲存的陣序`index`物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `index`  
  
## <a name="remarks"></a>備註  
 `index`結構表示的座標向量*N*指定中的唯一位置的整數*N*-維度空間。 在向量中的值為從最大顯著性到最小顯著性排序。 您可以擷取使用的元件值[運算子 =](#operator_eq)。  
  
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

_Array  
等級值的一維陣列。  
_I  
中的一維索引的索引位置。  
_I0  
最重要的維度的長度。  
_I1  
下一步-到-最高有效維度的長度。  
_I2  
最小顯著性維度的長度。  
_Other  
新的索引物件所依據的索引物件。  

## <a name="operator--"></a>  --運算子
遞減索引物件的每個項目。  
```  
index<_Rank>& operator--() restrict(amp,cpu);  

index operator--(
   int
) restrict(amp,cpu);
```  
### <a name="return-values"></a>傳回值
針對前置運算子，index 物件 (* 這)。 後置運算子，新的索引物件。

## <a name="operator_mod_eq"></a>  operator(mod) =   
該項目除以指定的數目時，會計算每個項目中的索引物件的模數 （餘數）。

```  
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```  
### <a name="parameters"></a>參數
_Rhs 要藉由分割模數的數字。
傳回值的索引物件。

## <a name="operator_star_eq"></a>  operator*=   
乘上每個項目中指定數目的索引物件。
```
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>參數
_Rhs 要相乘的數字。

## <a name="operator_div_eq"></a>  operator / = 
索引物件中的每個項目除以指定的數目。

```
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>參數
_Rhs 要除以的數字。

## <a name="operator_at"></a> operator\[\]  
傳回元件指定位置處的索引。

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
下列範例顯示元件的值索引。
```  
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>  operator++   
遞增索引物件的每個項目。
```  
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```  
### <a name="return-value"></a>傳回值
針對前置運算子，index 物件 (* 這)。 後置運算子，新的索引物件。

## <a name="operator_add_eq"></a>  operator+=   
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
將指定的索引物件的內容複製到這一個。
```  
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
``` 
### <a name="parameters"></a>參數
_Other 要複製的索引物件。

### <a name="return-value"></a>傳回值
此索引物件的參考。

## <a name="operator_-_eq"></a>  運算子 =
指定從數目減掉 index 物件的每個項目。
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

## <a name="rank"></a>  順位  
  取得 index 物件的順位。
```
static const int rank = _Rank;
``` 
## <a name="see-also"></a>另請參閱  
 [Concurrency 命名空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)

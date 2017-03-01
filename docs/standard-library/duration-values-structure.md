---
title: "duration_values 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chrono/std::chrono::duration_values
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 13
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8b0c02d4edc3a460f166cb65b312ef78337d403f
ms.lasthandoff: 02/24/2017

---
# <a name="durationvalues-structure"></a>duration_values 結構
提供 [duration](../standard-library/duration-class.md) 範本參數 `Rep` 的特定值。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Rep>  
struct duration_values;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[duration_values::max](#duration_values__max_method)|靜態。 指定 `Rep` 類型的值上限。|  
|[duration_values::min](#duration_values__min_method)|靜態。 指定 `Rep` 類型的值下限。|  
|[duration_values::zero](#duration_values__zero_method)|靜態。 傳回 `Rep(0)`。|  
  
## <a name="requirements"></a>需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
##  <a name="a-namedurationvaluesmaxmethoda--durationvaluesmax"></a><a name="duration_values__max_method"></a>  duration_values::max  
 靜態方法會傳回型別 `Ref` 的上限值。  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>傳回值  
 實際上，系統會傳回 `numeric_limits<Rep>::max()`。  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義的類型時，傳回的值必須大於 [duration_values::zero](#duration_values__zero_method)。  
  
##  <a name="a-namedurationvaluesminmethoda--durationvaluesmin"></a><a name="duration_values__min_method"></a>  duration_values::min  
 靜態方法會傳回型別 `Ref` 的下限值。  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>傳回值  
 實際上，系統會傳回 `numeric_limits<Rep>::lowest()`。  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義的類型時，傳回的值必須小於或等於 [duration_values::zero](#duration_values__zero_method)。  
  
##  <a name="a-namedurationvalueszeromethoda--durationvalueszero"></a><a name="duration_values__zero_method"></a>  duration_values::zero  
 傳回 `Rep(0)`。  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義型別時，傳回值必須代表加法類無限大。  
  
## <a name="see-also"></a>另請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)



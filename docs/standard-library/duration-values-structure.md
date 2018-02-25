---
title: "duration_values 結構 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
dev_langs:
- C++
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 996e0b02ade2f6c88c1f46ee9f84bbb28cfffdd7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="durationvalues-structure"></a>duration_values 結構
提供 [duration](../standard-library/duration-class.md) 範本參數 `Rep` 的特定值。  
  
## <a name="syntax"></a>語法  
  
```  
template <class Rep>  
struct duration_values;  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[max](#max)|靜態。 指定 `Rep` 類型的值上限。|  
|[min](#min)|靜態。 指定 `Rep` 類型的值下限。|  
|[zero](#zero)|靜態。 傳回 `Rep(0)`。|  
  
## <a name="requirements"></a>需求  
 **標頭：** \<chrono >  
  
 **命名空間：** std::chrono  
  
##  <a name="max"></a>  duration_values::max  
 靜態方法會傳回型別 `Ref` 的上限值。  
  
```  
static constexpr Rep max();
```  
  
### <a name="return-value"></a>傳回值  
 實際上，系統會傳回 `numeric_limits<Rep>::max()`。  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義的類型時，傳回的值必須大於 [duration_values::zero](#zero)。  
  
##  <a name="min"></a>  duration_values::min  
 靜態方法會傳回型別 `Ref` 的下限值。  
  
```  
static constexpr Rep min();
```  
  
### <a name="return-value"></a>傳回值  
 實際上，系統會傳回 `numeric_limits<Rep>::lowest()`。  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義的類型時，傳回的值必須小於或等於 [duration_values::zero](#zero)。  
  
##  <a name="zero"></a>  duration_values::zero  
 傳回 `Rep(0)`。  
  
```  
static constexpr Rep zero();
```  
  
### <a name="remarks"></a>備註  
 當 `Rep` 是使用者定義型別時，傳回值必須代表加法類無限大。  
  
## <a name="see-also"></a>請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono>](../standard-library/chrono.md)


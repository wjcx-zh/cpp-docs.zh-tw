---
title: "CDefaultCompareTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1d1253b7a7d69024465627cc9fb37fcd2afba693
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits 類別
這個類別會提供預設的比較函式項目。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|（靜態）呼叫此函式來比較兩個項目相等。|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|（靜態）呼叫此函式可判斷更高和較少的項目。|  
  
## <a name="remarks"></a>備註  
 這個類別包含兩個靜態函式來比較項目儲存在集合類別物件。 這個類別利用[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="compareelements"></a>CDefaultCompareTraits::CompareElements  
 呼叫此函式來比較兩個項目相等。  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>參數  
 `element1`  
 第一個元素。  
  
 `element2`  
 第二個項目中。  
  
### <a name="return-value"></a>傳回值  
 如果項目相等，false 否則，就會傳回 true。  
  
### <a name="remarks"></a>備註  
 此函式的預設實作是等號 ( `==`) 運算子。 物件的簡單資料型別以外，此函式可能需要覆寫。  
  
##  <a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered  
 呼叫此函式可判斷更高和較少的項目。  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>參數  
 `element1`  
 第一個元素。  
  
 `element2`  
 第二個項目中。  
  
### <a name="return-value"></a>傳回值  
 傳回整數，根據下表︰  
  
|條件|傳回值|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>備註  
 此函式的預設實作會使用`==`， ** \< **，和** > **運算子。 物件的簡單資料型別以外，此函式可能需要覆寫。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)


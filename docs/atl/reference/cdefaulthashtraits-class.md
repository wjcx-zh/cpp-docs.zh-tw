---
title: "CDefaultHashTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATL.CDefaultHashTraits<T>
- ATL::CDefaultHashTraits<T>
- ATL.CDefaultHashTraits
- ATL::CDefaultHashTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 5191327e5e60935829750c7d1e04ba89fcddc771
ms.lasthandoff: 02/24/2017

---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits 類別
這個類別提供靜態函式來計算雜湊值。  
  
## <a name="syntax"></a>語法  
  
```
template<typename T>  
class CDefaultHashTraits
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 若要儲存在集合中的資料類型。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDefaultHashTraits::Hash](#hash)|（靜態）呼叫此函式來計算雜湊值的指定項目。|  
  
## <a name="remarks"></a>備註  
 這個類別包含單一靜態函式會傳回指定項目的雜湊值。 這個類別利用[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="a-namehasha--cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash  
 呼叫此函式來計算雜湊值的指定項目。  
  
```
static ULONG Hash(const T& element) throw();
```  
  
### <a name="parameters"></a>參數  
 `element`  
 元素。  
  
### <a name="return-value"></a>傳回值  
 傳回雜湊值。  
  
### <a name="remarks"></a>備註  
 雜湊演算法的預設值是非常簡單︰ 傳回的值是項目數目。 如果需要更複雜的演算法，則會覆寫這個函式。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)


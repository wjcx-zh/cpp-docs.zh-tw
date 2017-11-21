---
title: "CDefaultHashTraits 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
dev_langs: C++
helpviewer_keywords: CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 383cdc49f9ac78447186a677bc712287b71b3994
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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
 這個類別包含單一的靜態函式，傳回指定之項目的雜湊值。 這個類別使用[CDefaultElementTraits 類別](../../atl/reference/cdefaultelementtraits-class.md)。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="hash"></a>CDefaultHashTraits::Hash  
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
 預設雜湊演算法是非常簡單： 傳回的值是項目數目。 如果需要更複雜的演算法，則會覆寫這個函式。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

---
title: "CComAutoDeleteCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CComAutoDeleteCriticalSection
- CComAutoDeleteCriticalSection
- ATL::CComAutoDeleteCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 17
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
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: eb53a0966d29759bbe7513f6042f72a280801707
ms.lasthandoff: 02/24/2017

---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 類別
這個類別提供方法來取得及釋放重要區段物件的擁有權。  
  
## <a name="syntax"></a>語法  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>備註  
 `CComAutoDeleteCriticalSection`衍生自類別[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 不過，`CComAutoDeleteCriticalSection`覆寫[詞彙](ccomsafedeletecriticalsection-class.md#term)方法`private`強制內部記憶體清除發生只有當此類別的執行個體超出範圍或明確從記憶體刪除的存取。  

  
 這個類別會介紹透過其基底類別沒有任何其他方法。 請參閱[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)和[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)如需有關重要區段的 helper 類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcore.h  
  
## <a name="see-also"></a>另請參閱  
 [CComSafeDeleteCriticalSection 類別](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


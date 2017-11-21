---
title: "CComAutoDeleteCriticalSection 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAutoDeleteCriticalSection
- atlcore/ATL::CComAutoDeleteCriticalSection
dev_langs: C++
helpviewer_keywords: CComAutoDeleteCriticalSection class
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d073e392030db72d6371a798875daf3d7a90e247
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ccomautodeletecriticalsection-class"></a>CComAutoDeleteCriticalSection 類別
這個類別會提供方法來取得及釋放重要區段物件的擁有權。  
  
## <a name="syntax"></a>語法  
  
```
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection
```  
  
## <a name="remarks"></a>備註  
 `CComAutoDeleteCriticalSection`衍生自類別[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)。 不過，`CComAutoDeleteCriticalSection`會覆寫[詞彙](ccomsafedeletecriticalsection-class.md#term)方法`private`存取，這會強制進行只有在這個類別的執行個體超出範圍或明確從記憶體中刪除的內部記憶體清除。  

  
 這個類別透過其基底類別引進任何額外的方法。 請參閱[CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)和[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)如需有關關鍵區段的 helper 類別。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcore.h  
  
## <a name="see-also"></a>另請參閱  
 [CComSafeDeleteCriticalSection 類別](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

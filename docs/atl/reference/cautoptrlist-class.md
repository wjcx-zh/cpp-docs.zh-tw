---
title: "CAutoPtrList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0887b0fdaeeaf498bacdc5eec66981656f34fed8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cautoptrlist-class"></a>CAutoPtrList 類別
建構的智慧型指標清單時，這個類別會提供有效的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename E>  
class CAutoPtrList : 
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```  
  
#### <a name="parameters"></a>參數  
 `E`  
 指標類型。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式，並衍生方法[CAtlList](../../atl/reference/catllist-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)協助清單物件儲存智慧型指標的建立。 類別[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)的陣列物件提供類似的功能。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cautoptrlist"></a>CAutoPtrList::CAutoPtrList  
 建構函式。  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小，預設值是 10。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的配置新的項目時所需數量的量值。 較大的區塊大小減少記憶體配置常式，呼叫，但使用較多資源。  
  
## <a name="see-also"></a>請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: b39c3c08cf2970036bf8690c46a4f3518a7a55e1
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

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
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式，且衍生方法從[CAtlList](../../atl/reference/catllist-class.md)和[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)協助儲存智慧型指標的清單物件的建立。 類別[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)的陣列物件提供類似的功能。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CAutoPtrList`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="cautoptrlist"></a>CAutoPtrList::CAutoPtrList  
 建構函式。  
  
```
CAutoPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小，預設值為 10。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的一種配置需要新的項目時數量。 較大的區塊大小減少記憶體配置常式，但使用較多資源。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CAutoPtrElementTraits 類別](../../atl/reference/cautoptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


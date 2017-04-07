---
title: "CHeapPtrList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 9acf18d0e0a72f27a335cefca81341c95d530ae5
ms.lasthandoff: 02/24/2017

---
# <a name="cheapptrlist-class"></a>CHeapPtrList 類別
建構堆積指標清單時，這個類別會提供有效的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<typename E, class Allocator = ATL::CCRTAllocator>  
class CHeapPtrList 
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```  
  
#### <a name="parameters"></a>參數  
 `E`  
 要儲存於集合類別的物件類型。  
  
 `Allocator`  
 要使用的記憶體配置類別。 預設值是[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式，且衍生方法從[CAtlList](../../atl/reference/catllist-class.md)和[CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)協助儲存堆積的指標集合類別物件的建立。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CHeapPtrList`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList  
 建構函式。  
  
```
CHeapPtrList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的一種配置需要新的項目時數量。 較大的區塊大小減少記憶體配置常式，但使用較多資源。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CHeapPtr 類別](../../atl/reference/cheapptr-class.md)   
 [CHeapPtrElementTraits 類別](../../atl/reference/cheapptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


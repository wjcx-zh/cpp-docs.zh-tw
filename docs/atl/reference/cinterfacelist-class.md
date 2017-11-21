---
title: "CInterfaceList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceList
- ATLCOLL/ATL::CInterfaceList
- ATLCOLL/ATL::CInterfaceList::CInterfaceList
dev_langs: C++
helpviewer_keywords: CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 86e92f86896ac7c5a06b73a68e2d6889d10ea87b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="cinterfacelist-class"></a>CInterfaceList 類別
建構 COM 介面指標的清單時，這個類別會提供有用的方法。  
  
## <a name="syntax"></a>語法  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 `I`  
 指定要儲存的指標類型的 COM 介面。  
  
 `piid`  
 指向 IID 的`I`。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|建構函式的介面清單。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式和衍生的方法來建立 COM 介面指標的清單。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)何時需要陣列。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cinterfacelist"></a>CInterfaceList::CInterfaceList  
 建構函式的介面清單。  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小，預設值是 10。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的配置新的項目時所需數量的量值。 較大的區塊大小減少記憶體配置常式，呼叫，但使用較多資源。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

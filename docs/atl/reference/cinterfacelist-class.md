---
title: "CInterfaceList 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CInterfaceList
- ATL.CInterfaceList
- CInterfaceList
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceList class
ms.assetid: 2077764d-25e5-4b3d-96c8-08a287bbcd25
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
ms.openlocfilehash: 50d86163080c5a0d0a7bb9ed6d77a40ac73722e7
ms.lasthandoff: 02/24/2017

---
# <a name="cinterfacelist-class"></a>CInterfaceList 類別
建構的 COM 介面指標清單時，這個類別會提供有效的方法。  
  
## <a name="syntax"></a>語法  
  
```
template<class I, const IID* piid =& __uuidof(I)>  
class CInterfaceList 
   : public CAtlList<ATL::CComQIPtr<I, piid>,
                     CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 `I`  
 COM 介面，指定要儲存的指標的類型。  
  
 `piid`  
 指標的 IID `I`。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInterfaceList::CInterfaceList](#cinterfacelist)|建構函式的介面清單。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式和衍生的方法來建立 COM 介面指標的清單。 使用[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)陣列時所需。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CAtlList](../../atl/reference/catllist-class.md)  
  
 `CInterfaceList`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="a-namecinterfacelista--cinterfacelistcinterfacelist"></a><a name="cinterfacelist"></a>CInterfaceList::CInterfaceList  
 建構函式的介面清單。  
  
```
CInterfaceList(UINT nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>參數  
 `nBlockSize`  
 區塊大小，預設值為 10。  
  
### <a name="remarks"></a>備註  
 區塊大小是記憶體的一種配置需要新的項目時數量。 較大的區塊大小減少記憶體配置常式，但使用較多資源。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlList 類別](../../atl/reference/catllist-class.md)   
 [CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


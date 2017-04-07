---
title: "CInterfaceArray 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray
- ATLCOLL/ATL::CInterfaceArray::CInterfaceArray
dev_langs:
- C++
helpviewer_keywords:
- CInterfaceArray class
ms.assetid: 1f29cf66-a086-4a7b-b6a8-64f73da39f79
caps.latest.revision: 18
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
ms.openlocfilehash: a2a99eb3cff4f2381d4c58e4d1a7aaa167e83896
ms.lasthandoff: 02/24/2017

---
# <a name="cinterfacearray-class"></a>CInterfaceArray 類別
建構 COM 介面指標的陣列時，這個類別會提供有效的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 `I`  
 COM 介面，指定要儲存的指標的類型。  
  
 `piid`  
 指標的 IID `I`。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|介面陣列建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式和衍生的方法來建立 COM 介面指標的陣列。 使用[CInterfaceList](../../atl/reference/cinterfacelist-class.md)清單時所需。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlcoll.h  
  
##  <a name="cinterfacearray"></a>CInterfaceArray::CInterfaceArray  
 建構函式。  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化智慧型指標的陣列。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlArray 類別](../../atl/reference/catlarray-class.md)   
 [CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)


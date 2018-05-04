---
title: CInterfaceArray 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36a24eadea87d0d34adf0f577b321fa16a7cfc86
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="cinterfacearray-class"></a>CInterfaceArray 類別
建構 COM 介面指標的陣列時，這個類別會提供有用的方法。  
  
## <a name="syntax"></a>語法  
  
```
template <class I, const IID* piid=& __uuidof(I)>  
class CInterfaceArray : 
   public CAtlArray<ATL::CComQIPtr<I, piid>,
                    CComQIPtrElementTraits<I, piid>>
```  
  
#### <a name="parameters"></a>參數  
 `I`  
 指定要儲存的指標類型的 COM 介面。  
  
 `piid`  
 指向 IID 的`I`。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CInterfaceArray::CInterfaceArray](#cinterfacearray)|介面陣列建構函式。|  
  
## <a name="remarks"></a>備註  
 這個類別提供建構函式和衍生的方法來建立 COM 介面指標的陣列。 使用[CInterfaceList](../../atl/reference/cinterfacelist-class.md)清單時所需。  
  
 如需詳細資訊，請參閱[ATL 集合類別](../../atl/atl-collection-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CAtlArray`  
  
 `CInterfaceArray`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlcoll.h  
  
##  <a name="cinterfacearray"></a>  CInterfaceArray::CInterfaceArray  
 建構函式。  
  
```
CInterfaceArray() throw();
```  
  
### <a name="remarks"></a>備註  
 初始化智慧型指標陣列。  
  
## <a name="see-also"></a>另請參閱  
 [CAtlArray 類別](../../atl/reference/catlarray-class.md)   
 [CComQIPtr 類別](../../atl/reference/ccomqiptr-class.md)   
 [CComQIPtrElementTraits 類別](../../atl/reference/ccomqiptrelementtraits-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

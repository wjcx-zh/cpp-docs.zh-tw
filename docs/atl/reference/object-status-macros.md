---
title: "物件狀態巨集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
caps.latest.revision: 16
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 433a816b19690f22f482f26f6ab70c73ed102673
ms.lasthandoff: 02/24/2017

---
# <a name="object-status-macros"></a>物件狀態巨集
這個巨集會設定屬於 ActiveX 控制項的旗標。  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|在 ATL ActiveX 控制項中用來設定**OLEMISC**旗標。|  

## <a name="requirements"></a>需求  
 **標頭︰**於 atlcom.h  

##  <a name="a-namedeclareolemiscstatusa--declareolemiscstatus"></a><a name="declare_olemisc_status"></a>DECLARE_OLEMISC_STATUS  
 使用 ATL ActiveX 控制項中設定 OLEMISC 旗標。  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>參數  
 *miscstatus*  
 所有適用的 OLEMISC 旗標。  
  
### <a name="remarks"></a>備註  
 這個巨集用來設定 ActiveX 控制項的 OLEMISC 旗標。 請參閱[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)如需詳細資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing #&124;](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)


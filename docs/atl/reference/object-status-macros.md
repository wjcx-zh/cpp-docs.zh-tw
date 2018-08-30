---
title: 物件狀態巨集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OLEMISC_STATUS
dev_langs:
- C++
ms.assetid: 727dbef2-a342-4157-9d64-a421805d9747
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fcfffcd9508876399b30238cac0b4f65c92c733
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206497"
---
# <a name="object-status-macros"></a>物件狀態巨集
這個巨集設定屬於 ActiveX 控制項的旗標。  
  
|||  
|-|-|  
|[DECLARE_OLEMISC_STATUS](#declare_olemisc_status)|用於 ATL ActiveX 控制項，以設定 OLEMISC 旗標。|  

## <a name="requirements"></a>需求  
 **標頭：** atlcom.h  

##  <a name="declare_olemisc_status"></a>  DECLARE_OLEMISC_STATUS  
 用於 ATL ActiveX 控制項，以設定 OLEMISC 旗標。  
  
```
DECLARE_OLEMISC_STATUS( miscstatus )
```  
  
### <a name="parameters"></a>參數  
 *miscstatus*  
 所有適用的 OLEMISC 旗標。  
  
### <a name="remarks"></a>備註  
 這個巨集用來設定 ActiveX 控制項的 OLEMISC 旗標。 請參閱[IOleObject::GetMiscStatus](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-getmiscstatus)如需詳細資訊。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_ATL_Windowing#124](../../atl/codesnippet/cpp/object-status-macros_1.h)]  
  
## <a name="see-also"></a>另請參閱  
 [巨集](../../atl/reference/atl-macros.md)

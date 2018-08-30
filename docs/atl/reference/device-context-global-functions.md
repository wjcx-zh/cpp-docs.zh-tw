---
title: 裝置內容全域函式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlwin/ATL::AtlCreateTargetDC
dev_langs:
- C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8944ecdb4f9996800264986a7a687df6020b0591
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209929"
---
# <a name="device-context-global-functions"></a>裝置內容全域函式
此函式會建立指定的裝置的裝置內容。  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|建立裝置內容。|  
  
##  <a name="atlcreatetargetdc"></a>  AtlCreateTargetDC  
 建立裝置內容中指定的裝置[DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice)結構。  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>參數  
 *hdc*  
 [in]現有的控制代碼的裝置內容，則為 NULL。  
  
 *ptd*  
 [in]指標`DVTARGETDEVICE`結構，其中包含目標裝置的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 中指定的裝置的裝置內容中傳回的控制代碼`DVTARGETDEVICE`。 如果未不指定任何裝置，則傳回預設顯示裝置的控制代碼。  
  
### <a name="remarks"></a>備註  
 如果結構為 NULL 並*hdc*為 NULL，會建立預設顯示裝置的裝置內容。  
  
 如果*hdc*不是 NULL 並*ptd*是 NULL，則函數會傳回現有*hdc*。  

## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
   
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

---
title: "裝置內容的全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlwin/ATL::AtlCreateTargetDC
dev_langs: C++
ms.assetid: 08ec28f6-daff-4882-9544-e8a4639d05c4
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d2560043bc97c384846696b76d8e38b459ae4a34
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="device-context-global-functions"></a>裝置內容的全域函式
此函式會建立指定裝置的裝置內容。  
  
|||  
|-|-|  
|[AtlCreateTargetDC](#atlcreatetargetdc)|建立裝置內容。|  
  
##  <a name="atlcreatetargetdc"></a>AtlCreateTargetDC  
 建立裝置內容中指定的裝置[DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613)結構。  
  
```
HDC AtlCreateTargetDC(HDC hdc, DVTARGETDEVICE* ptd);
```  
  
### <a name="parameters"></a>參數  
 *hdc*  
 [in]現有的控制代碼的裝置內容，或**NULL**。  
  
 `ptd`  
 [in]指標**DVTARGETDEVICE**結構，其中包含目標裝置的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回在指定的裝置的裝置內容的控制代碼**DVTARGETDEVICE**。 如果未不指定任何裝置，則傳回預設顯示裝置的控制代碼。  
  
### <a name="remarks"></a>備註  
 如果結構是**NULL**和*hdc*是**NULL**，會建立預設顯示裝置的裝置內容。  
  
 如果*hdc*不**NULL**和`ptd`是**NULL**，此函數會傳回現有*hdc*。  

## <a name="requirements"></a>需求  
 **標頭：** atlwin.h  
   
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

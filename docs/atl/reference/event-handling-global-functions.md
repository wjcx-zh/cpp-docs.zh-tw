---
title: "事件處理全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: atlbase/ATL::AtlWaitWithMessageLoop
dev_langs: C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 747704bb271c294728832c8ee8108da458c739ba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="event-handling-global-functions"></a>事件處理全域函式
此函式提供的事件處理常式。  
  
> [!IMPORTANT]
>  下表所列的函式不能在 Windows 執行階段中執行的應用程式。  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等候發出物件通知，同時視需要分派視窗訊息。|  

## <a name="requirements"></a>需求  
 **標頭：** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
 等候發出物件通知，同時視需要分派視窗訊息。  
  
> [!IMPORTANT]
>  此函式不能在 Windows 執行階段中執行的應用程式。  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>參數  
 `hEvent`  
 [in]要等候的物件控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果物件已收到訊號。  
  
### <a name="remarks"></a>備註  
 如果您想要等候的物件事件，就可能發生，且會通知發生，但允許在等待時分派視窗訊息，這非常有用。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)

---
title: "事件處理全域函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4bf2a8b0211361f5d5d2bf0f996e978638631116
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="event-handling-global-functions"></a>事件處理全域函式
此函數會提供事件處理常式。  
  
> [!IMPORTANT]
>  下表所列的函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等候發出物件通知，同時視需要分派視窗訊息。|  

## <a name="requirements"></a>需求  
 **標頭︰** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop  
 等候發出物件通知，同時視需要分派視窗訊息。  
  
> [!IMPORTANT]
>  此函式不能在執行中的應用程式[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>參數  
 `hEvent`  
 [in]要等候的物件控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果物件已收到訊號。  
  
### <a name="remarks"></a>備註  
 如果您想要等候的物件事件會發生此問題，會通知發生，但允許在等待時分派視窗訊息，這非常有用。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../atl/reference/atl-functions.md)


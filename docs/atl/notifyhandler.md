---
title: "NotifyHandler |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyHandler
dev_langs: C++
helpviewer_keywords: NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ea725b470d08688ed824991d308677970e2c8277
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="notifyhandler"></a>NotifyHandler
函式的第三個參數所識別的名稱`NOTIFY_HANDLER`中訊息對應巨集。  
  
## <a name="syntax"></a>語法  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>參數  
 `idCtrl`  
 傳送訊息之控制項的識別項。  
  
 *pnmh*  
 位址[NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514)結構，其中包含通知程式碼和其他資訊。 對於某些通知的訊息，此參數會指向具有較大結構**NMHDR**結構做為其第一個成員。  
  
 `bHandled`  
 訊息對應集`bHandled`至**TRUE**之前*NotifyHandler*呼叫。 如果*NotifyHandler*完全不會處理訊息，它應該設定`bHandled`至**FALSE**以指出需要進一步處理的訊息。  
  
## <a name="return-value"></a>傳回值  
 訊息處理的結果。 0，表示成功。  
  
## <a name="remarks"></a>備註  
 如需訊息對應中使用此訊息處理常式的範例，請參閱[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。  
  
## <a name="see-also"></a>另請參閱  
 [實作視窗](../atl/implementing-a-window.md)   
 [訊息對應](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


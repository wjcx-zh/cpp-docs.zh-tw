---
title: MessageHandler |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74a5e50eae425340bcb0f9a455422b43db0be0b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207106"
---
# <a name="messagehandler"></a>MessageHandler
`MessageHandler` 是 MESSAGE_HANDLER 巨集訊息對應中的第二個參數所識別的函式的名稱。  
  
## <a name="syntax"></a>語法  
  
```  
 
    LRESULT 
    MessageHandler 
 (
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>參數  
 *uMsg*  
 指定的訊息。  
  
 *wParam*  
 其他特定訊息資訊。  
  
 *lParam*  
 其他特定訊息資訊。  
  
 *bHandled*  
 訊息對應集*bHandled*設為 TRUE 之前`MessageHandler`呼叫。 如果`MessageHandler`完全不會處理訊息，它應該設定*bHandled*為 FALSE，以指出需要進一步處理的訊息。  
  
## <a name="return-value"></a>傳回值  
 訊息處理的結果。 0，表示成功。  
  
## <a name="remarks"></a>備註  
 如需訊息對應中使用此訊息處理常式的範例，請參閱[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。  
  
## <a name="see-also"></a>另請參閱  
 [實作視窗](../atl/implementing-a-window.md)   
 [訊息對應](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)


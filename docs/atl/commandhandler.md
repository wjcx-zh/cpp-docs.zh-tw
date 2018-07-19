---
title: CommandHandler |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 784551b090f7c0c73b96b846fcc8d74017cc1e30
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850637"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` 訊息對應中 COMMAND_HANDLER 巨集的第三個參數所識別的函式。  
  
## <a name="syntax"></a>語法  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>參數  
 *wNotifyCode*  
 通知的程式碼。  
  
 *wID*  
 功能表項目、 控制項或加速器的識別項。  
  
 *hWndCtl*  
 視窗控制項的控制代碼。  
  
 *bHandled*  
 訊息對應集*bHandled*設為 TRUE 之前`CommandHandler`呼叫。 如果`CommandHandler`完全不會處理訊息，它應該設定*bHandled*為 FALSE，以指出需要進一步處理的訊息。  
  
## <a name="return-value"></a>傳回值  
 訊息處理的結果。 0，表示成功。  
  
## <a name="remarks"></a>備註  
 如需訊息對應中使用此訊息處理常式的範例，請參閱[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。  
  
## <a name="see-also"></a>另請參閱  
 [實作視窗](../atl/implementing-a-window.md)   
 [訊息對應](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)


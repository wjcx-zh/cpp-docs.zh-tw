---
title: 無底邊 Rich Edit 控制項 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9e3115000b7b45d9b48a1ac0d274eb32c11f4d0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43218875"
---
# <a name="bottomless-rich-edit-controls"></a>無底邊 Rich Edit 控制項
您的應用程式可以調整 rich edit 控制項的大小 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 視需要因此它一律是做為其內容的相同大小。 Rich edit 控制項支援此所謂的 「 無底邊 」 功能，藉由傳送其父視窗[EN_REQUESTRESIZE](/windows/desktop/Controls/en-requestresize)每當其內容的大小變更的通知訊息。  
  
 處理時**EN_REQUESTRESIZE**通知訊息時，應用程式應該調整大小的控制項中指定的維度[REQRESIZE](/windows/desktop/api/richedit/ns-richedit-_reqresize)結構。 應用程式可能也會移動控制項附近的任何資訊，以配合控制項的高度變更。 若要調整控制項的大小，您可以使用`CWnd`函式[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 您可以強制無底邊 rich edit 控制項傳送**EN_REQUESTRESIZE**使用的通知訊息[En_requestresize](../mfc/reference/cricheditctrl-class.md#requestresize)成員函式。 此訊息可用於[OnSize](../mfc/reference/cwnd-class.md#onsize)處理常式。  
  
 若要接收**EN_REQUESTRESIZE**通知訊息，您必須使用啟用通知`SetEventMask`成員函式。  
  
## <a name="see-also"></a>另請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)


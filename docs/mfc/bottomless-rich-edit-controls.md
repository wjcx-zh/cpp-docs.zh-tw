---
title: "無底邊 Rich Edit 控制項 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- bottomless rich edit controls
- rich edit controls [MFC], bottomless
- CRichEditCtrl class [MFC], bottomless
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f8a92b180ed44937c29cd880dea7439e0cfe20b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="bottomless-rich-edit-controls"></a>無底邊 Rich Edit 控制項
您的應用程式可以調整 rich edit 控制項的大小 ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) 視需要因此一律會做為其內容的大小相同。 Rich edit 控制項傳送給其父視窗支援此所謂的 「 無底邊 」 功能[EN_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983)每當其內容的大小變更的通知訊息。  
  
 處理時**EN_REQUESTRESIZE**通知訊息時，應用程式應該調整控制項中指定的維度[REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950)結構。 應用程式可能也會移動控制項附近的任何資訊，以配合控制項的高度變更。 若要調整控制項的大小，您可以使用`CWnd`函式[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 您可以強制無底邊 rich edit 控制項傳送**EN_REQUESTRESIZE**通知訊息使用[En_requestresize](../mfc/reference/cricheditctrl-class.md#requestresize)成員函式。 此訊息可用於[OnSize](../mfc/reference/cwnd-class.md#onsize)處理常式。  
  
 若要接收**EN_REQUESTRESIZE**通知訊息，您必須使用啟用通知`SetEventMask`成員函式。  
  
## <a name="see-also"></a>請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)


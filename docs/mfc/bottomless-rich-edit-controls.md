---
title: "無底邊 Rich Edit 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "無底邊 Rich Edit 控制項"
  - "CRichEditCtrl 類別, 無底邊"
  - "Rich Edit 控制項, 無底邊"
ms.assetid: 2877dd32-1e9a-4fd1-98c0-66dcbbeef1de
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 無底邊 Rich Edit 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的應用程式可以調整大小的 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)，因為需要，讓它永遠都是相同大小與其內容。  Rich Edit 控制項傳送其父視窗支援這種所謂的無底的功能 [EN\_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787983) 通知訊息，當其內容大小變更。  
  
 當處理 **EN\_REQUESTRESIZE** 通知訊息時，應用程式應該調整大小的控制項加入至指定的 [REQRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb787950) 結構的維度。  應用程式在高度可能在控制項周圍也將所有資訊容納變更。  若要調整控制項大小，您可以使用 `CWnd` 函式 [SetWindowPos](../Topic/CWnd::SetWindowPos.md)。  
  
 使用 [RequestResize](../Topic/CRichEditCtrl::RequestResize.md) 成員函式，強制未結束的 Rich Edit 控制項傳送 **EN\_REQUESTRESIZE** 通知訊息。  這個訊息可以適用於 [OnSize](../Topic/CWnd::OnSize.md) 處理常式。  
  
 使用 `SetEventMask` 成員函式，要收到 **EN\_REQUESTRESIZE** 通知訊息，您必須啟用告知。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
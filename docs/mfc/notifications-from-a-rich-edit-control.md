---
title: "來自 Rich Edit 控制項的告知 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl 類別, 告知"
  - "訊息, 告知"
  - "告知, 從 CRichEditCtrl"
  - "Rich Edit 控制項, 告知"
ms.assetid: eb5304fe-f4f3-4557-9ebf-3095dea383c4
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 來自 Rich Edit 控制項的告知
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通知訊息回報影響 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的事件。  使用訊息反映，它們可以處理由父視窗，或者，由 Rich Edit 控制項。  Rich Edit 控制項支援所有通知訊息使用與編輯控制項以及許多其他部分。  您可以判斷哪些通知訊息的 Rich Edit 控制項將其事件遮罩傳送其父視窗」。  
  
 要設定的 Rich Edit 控制項的事件遮罩，請使用 [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) 成員函式。  使用 [GetEventMask](../Topic/CRichEditCtrl::GetEventMask.md) 成員函式，擷取 Rich Edit 控制項的事件遮罩。  
  
 以下各節列出幾個特定告知及其用法:  
  
-   處理 **EN\_MSGFILTER** 通知的**EN\_MSGFILTER** 讓類別， Rich Edit 控制項或其父視窗，篩選，所有鍵盤和滑鼠輸入到控制項。  處理常式防止鍵盤或滑鼠訊息處理或可以修改指定的 [MSGFILTER](http://msdn.microsoft.com/library/windows/desktop/bb787936) 結構變更訊息。  
  
-   **EN\_PROTECTED** 控制代碼偵測使用者何時 **EN\_PROTECTED** 的通知訊息嘗試修改保護的文字。  若要將文字範圍為 protected，您可以設定保護的字元作用。  如需詳細資訊，請參閱 [在 Rich Edit 控制項的字元格式。](../mfc/character-formatting-in-rich-edit-controls.md)。  
  
-   **EN\_DROPFILES** 您可以讓使用者藉由處理 **EN\_DROPFILES** 通知訊息放置在 Rich Edit 控制項的檔案。  將指定的 [ENDROPFILES](http://msdn.microsoft.com/library/windows/desktop/bb787895) 結構包含置放之檔案的相關資訊。  
  
-   **EN\_SELCHANGE** 應用程式無法偵測到目前的選取範圍時會處理 **EN\_SELCHANGE** 通知訊息變更。  通知訊息指定包含新選取範圍的 [SELCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb787952) 結構資訊。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
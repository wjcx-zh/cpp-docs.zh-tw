---
title: "Rich Edit 控制項中的字元格式化 | Microsoft Docs"
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
  - "CRichEditCtrl 類別, 其中的字元格式化"
  - "格式化 [C++], 字元"
  - "Rich Edit 控制項, 其中的字元格式化"
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控制項中的字元格式化
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的成員函式為格式字元和擷取格式化資訊。  對於字元，您可以指定字樣，調整，色彩和效果，例如粗體、斜體，並保護。  
  
 使用 [SetSelectionCharFormat](../Topic/CRichEditCtrl::SetSelectionCharFormat.md) 和 [SetWordCharFormat](../Topic/CRichEditCtrl::SetWordCharFormat.md) 成員函式，您可以將字元格式。  若要判斷所選取文字的目前字元格式，請使用 [GetSelectionCharFormat](../Topic/CRichEditCtrl::GetSelectionCharFormat.md) 成員函式。  [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) 結構用來以這些成員函式指定字元屬性。  其中一個 **CHARFORMAT** 的重要成員是 **dwMask**。  在 `SetSelectionCharFormat` 和 `SetWordCharFormat`， **dwMask** 指定哪些字元屬性會由這個函式呼叫設定。  `GetSelectionCharFormat` 報告第一個字元的屬性在選取範圍中; **dwMask** 指定一致的選取範圍中的屬性。  
  
 您也可以取得及設定預設字元格式，而是格式套用至所有後續插入的字元。  例如，在中，如果應用程式將格式化為粗體預設字元，而且使用者會輸入字元，該字元為粗體。  若要取得和設定預設字元格式，使用 [GetDefaultCharFormat](../Topic/CRichEditCtrl::GetDefaultCharFormat.md) 和 [SetDefaultCharFormat](../Topic/CRichEditCtrl::SetDefaultCharFormat.md) 成員函式。  
  
 「protected」字元屬性不變更文字的外觀。  如果使用者嘗試修改保護的文字， Rich Edit 控制項傳送給其父視窗 **EN\_PROTECTED** 通知訊息，讓父視窗允許或防止變更。  使用 [SetEventMask](../Topic/CRichEditCtrl::SetEventMask.md) 成員函式，要接收這個告知訊息，您必須啟用它。  如需事件遮罩的詳細資訊，請參閱 [從 Rich Edit 控制項的告知。](../mfc/notifications-from-a-rich-edit-control.md)，稍後在本主題中。  
  
 前景色彩是字元屬性，不過，背景色彩是 Rich Edit 控制項的屬性。  若要設定背景色彩，請使用 [SetBackgroundColor](../Topic/CRichEditCtrl::SetBackgroundColor.md) 成員函式。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
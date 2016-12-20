---
title: "Rich Edit 控制項的概觀 | Microsoft Docs"
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
  - "Rich Edit 控制項"
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控制項的概觀
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!IMPORTANT]
>  如果您在對話方塊使用 Rich Edit 控制項 \(不論應用程式是 SDI、MDI 或對話方塊架構\)，在對話方塊顯示之前您必須一次呼叫 [AfxInitRichEdit](../Topic/AfxInitRichEdit.md)。  呼叫這個函式的一般位置在程式的 `InitInstance` 成員函式。  您不需要在要每次顯示對話方塊時呼叫它，只需在第一次。  如果您使用 `CRichEditView`，不需要呼叫 `AfxInitRichEdit` 。  
  
 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 提供用來格式化文字的程式設計介面。  然而，應用程式必須實作所有必要的使用者介面元件讓使用者能夠執行格式化作業。  Rich Edit 控制項支援變更選取文字中的字元或段落屬性。  字元屬性的範例為粗體，斜體、字型系列和字型大小。  段落屬性的範例包括對齊、邊界和定位停駐點。  不過，它是由提供使用者介面的您決定，如工具列按鈕、功能表項目或格式字元對話方塊。  也有查詢目前選取範圍中 Rich Edit 控制項的屬性的函式。  請使用這些函式顯示屬性的目前設定，例如，如果選取範圍有一個粗體字元格式屬性，在命令 UI 設定一個核取記號。  
  
 如需字元和段落格式的詳細資訊，請參閱 [字元格式](../mfc/character-formatting-in-rich-edit-controls.md) 和 [段落格式](../mfc/paragraph-formatting-in-rich-edit-controls.md) 主題。  
  
 Rich Edit 控制項支援使用的大部分的作業和通知訊息與多行編輯控制項。  因此，已使用編輯控制項的應用程式可以隨時轉換成使用 Rich Edit 控制項。  其他訊息和通知讓應用程式能夠存取 Rich Edit 控制項的獨特功能。  如需編輯控制項的詳細資訊，請參閱[CEdit](../mfc/reference/cedit-class.md)。  
  
 如需通知的詳細資訊，請參閱本主題稍後的 [來自 Rich Edit 控制項的通知](../mfc/notifications-from-a-rich-edit-control.md)。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
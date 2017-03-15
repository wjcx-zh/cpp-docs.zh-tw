---
title: "Rich Edit 控制項中的剪貼簿流作業 | Microsoft Docs"
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
  - "剪貼簿, CRichEditCtrl 中的作業"
  - "Rich Edit 控制項中的複製作業"
  - "CRichEditCtrl 類別, 剪貼簿作業"
  - "CRichEditCtrl 類別, 貼上作業"
  - "CRichEditCtrl 類別中的剪下作業"
  - "貼上剪貼簿資料"
  - "Rich Edit 控制項, 剪貼簿作業"
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Rich Edit 控制項中的剪貼簿流作業
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您的應用程式可貼上剪貼簿的內容貼至 Rich 編輯控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 使用的最佳可用剪貼簿格式或特定剪貼簿格式。  您也可以判斷 Rich 編輯控制項是否可以貼上剪貼簿格式。  
  
 使用 [複製](../Topic/CRichEditCtrl::Copy.md) 或 [剪下](../Topic/CRichEditCtrl::Cut.md) 成員函式，您可以複製或剪下目前選取範圍的內容。  同樣地，使用 [貼上](../Topic/CRichEditCtrl::Paste.md) 成員函式，可以將剪貼簿內容貼入 Rich 編輯控制項。  控制項將它辨識，依據假設最描述格式的第一個可用的格式。  
  
 要貼上的特定剪貼簿格式，您可以使用 [PasteSpecial](../Topic/CRichEditCtrl::PasteSpecial.md) 成員函式。  這個函式以讓使用者選取剪貼簿格式的選擇性貼上命令的應用程式。  您可以使用 [CanPaste](../Topic/CRichEditCtrl::CanPaste.md) 成員函式來判斷指定格式是否由控制項辨識。  
  
 您也可以使用 `CanPaste` 來判斷是否有可用的剪貼簿格式是否由 Rich 編輯控制項辨識。  這個函式適用於 `OnInitMenuPopup` 處理常式。  應用程式可能會啟用還是灰色其貼上命令視控制項是否可貼上任何可用的格式。  
  
 Rich 編輯控制項註冊兩剪貼簿格式:RTF 格式和呼叫 RichEdit 文字和物件。  您可以使用 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) 函式，應用程式可以註冊這些格式，指定 **CF\_RTF** 和 **CF\_RETEXTOBJ** 值。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
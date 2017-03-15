---
title: "Rich Edit 控制項中的列印 | Microsoft Docs"
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
  - "CRichEditCtrl 類別, 列印"
  - "列印 [MFC], CRichEditCtrl"
  - "Rich Edit 控制項, 列印"
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Rich Edit 控制項中的列印
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以通知 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 呈現它的指定裝置的輸出，例如印表機。  您也可以指定 Rich Edit 控制項格式化其文字輸出裝置。  
  
 若要格式化一部分的 Rich Edit 控制項的內容特定裝置的，您可以使用 [FormatRange](../Topic/CRichEditCtrl::FormatRange.md) 成員函式。  [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) 結構搭配此函式指定文字範圍格式以及目標裝置的裝置內容 \(Device \(DC\)。  
  
 使用 [DisplayBand](../Topic/CRichEditCtrl::DisplayBand.md) 成員函式，在格式化輸出裝置的文字後，您可以將輸出傳送至裝置。  使用 `FormatRange` 和 `DisplayBand`，由重複，列印的應用程式的 Rich Edit 控制項的內容可以實作行帶效果。\(條件帶作用為列印目的匯出分割成較小的部分\)。  
  
 您可以使用 [SetTargetDevice](../Topic/CRichEditCtrl::SetTargetDevice.md) 成員函式指定 Rich Edit 控制項將它格式化文字的目標裝置。  此函式為 WYSIWYG \(所見即所得 \(WYSIWYG\) 您取得\) 格式是有用的，應用程式將文字使用預設印表機的字型度量資訊而非螢幕的。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
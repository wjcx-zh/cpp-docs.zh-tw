---
title: "與 Rich Edit 控制項相關的類別 | Microsoft Docs"
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
  - "類別 [C++], 與 Rich Edit 控制項相關"
  - "CRichEditCtrl 類別, 相關類別"
  - "CRichEditCtrlItem 類別和 CRichEditCtrl"
  - "CRichEditDoc 類別, Rich Edit 控制項"
  - "CRichEditView 類別, 和 CRichEditCtrl"
  - "Rich Edit 控制項, 和 CRichEditDoc"
  - "Rich Edit 控制項, 和 CRichEditItem"
  - "Rich Edit 控制項, 和 CRichEditView"
  - "Rich Edit 控制項, 與其相關的類別"
ms.assetid: 4b31c2cc-6ea1-4146-b7c5-b0b5b419f14d
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 與 Rich Edit 控制項相關的類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CRichEditView](../mfc/reference/cricheditview-class.md)、 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)和 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md) 類別在 MFC 的文件\/檢視架構內提供 Rich Edit 控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) 的功能。  `CRichEditView` 會維護文字和格式一般文字。  `CRichEditDoc` 會在這個檢視 OLE 用戶端項目的清單。  `CRichEditCntrItem` 提供容器的存取 OLE 用戶端項目。  若要修改 `CRichEditView`的內容，請使用 [CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md) 來存取基礎 Rich Edit 控制項。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
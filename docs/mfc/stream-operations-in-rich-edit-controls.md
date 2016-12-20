---
title: "Rich Edit 控制項中的資料流作業 | Microsoft Docs"
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
  - "CRichEditCtrl 類別, 資料流作業"
  - "CRichEditCtrl 類別, 資料流儲存體"
  - "Rich Edit 控制項, 資料流作業"
  - "儲存體, CRichEditCtrl 中的資料流"
  - "CRichEditCtrl 中的資料流作業"
  - "資料流儲存體和 CRichEditCtrl"
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rich Edit 控制項中的資料流作業
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用資料流傳送資料至或從 Rich 編輯控制項 \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\)。  資料流是由 [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) 結構中定義的，指定緩衝區和應用程式定義的回呼函式。  
  
 若要將資料讀入 Rich Edit 控制項 \(即資料流資料\)，請使用 [StreamIn](../Topic/CRichEditCtrl::StreamIn.md) 成員函式。  控制項會重複呼叫應用程式定義的回呼函式時，都會將資料的區段加入至緩衝區。  
  
 要儲存的 Rich Edit 控制項的內容 \(也就是資料流資料\)，您可以使用 [StreamOut](../Topic/CRichEditCtrl::StreamOut.md) 成員函式。  控制項將資料寫入重複撰寫並呼叫應用程式定義的回呼函式。  針對每個呼叫，回呼函式儲存緩衝區的內容。  
  
## 請參閱  
 [使用 CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [控制項](../mfc/controls-mfc.md)
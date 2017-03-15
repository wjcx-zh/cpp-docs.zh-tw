---
title: "Setting the Width of a Horizontal Scroll Bar | Microsoft Docs"
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
  - "list controls, scroll bar width"
  - "CListBox::SetHorizontalExtent"
  - "controls [C++], scroll bar"
  - "scroll bars, displaying in controls"
  - "horizontal scroll bar width"
  - "CListBox class, scroll bar width"
  - "scroll bars, width"
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Setting the Width of a Horizontal Scroll Bar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您使用 MFC 類別將一個具有水平捲軸的清單方塊加入至對話方塊時，捲軸不會自動出現在您的應用程式中。  
  
### 若使讓捲軸出現  
  
1.  在您的程式碼中呼叫 [CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md) 來為最寬的項目設定最大寬度。  
  
     不設定這個值，捲軸不會出現，即使清單方塊中的項目比方塊寬。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 MFC  
  
## 請參閱  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控制項](../mfc/controls-mfc.md)
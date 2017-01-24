---
title: "Toolbar Button Properties | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "size, toolbar buttons"
  - "toolbar buttons (in Toolbar editor), setting properties"
  - "Toolbar editor, toolbar button properties"
  - "status bars, active toolbar button text"
  - "command IDs, toolbar buttons"
  - "width, toolbar buttons"
ms.assetid: b2705814-7c5d-4f24-8f77-07559b0cdda2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Toolbar Button Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

工具列按鈕的屬性：  
  
|屬性|描述|  
|--------|--------|  
|**ID**|定義按鈕的 ID。  下拉式清單提供了常用的 **ID** 名稱。|  
|**Width**|設定按鈕的寬度。  建議採用 16 像素。|  
|**Height**|設定按鈕的高度。  請注意，改變一個按鈕的高度將改變工具列所有按鈕的高度。  建議採用 15 像素。|  
|**提示**|定義顯示於狀態列的訊息。  加入 \\n 和一個名稱，可將工具提示加入工具列按鈕。  如需詳細資訊，請參閱[建立工具提示](../mfc/creating-a-tool-tip-for-a-toolbar-button.md)。|  
  
 **Width** 和 **Height** 會套用至所有按鈕。  用來建立工具列的點陣圖最多可容許 2048 的寬度。  因此，如果您將按鈕寬度設成 512，您只能有四個按鈕，如果將寬度設成 513，則只能有三個按鈕。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 MFC 或 ATL  
  
## 請參閱  
 [Changing the Properties of a Toolbar Button](../mfc/changing-the-properties-of-a-toolbar-button.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)
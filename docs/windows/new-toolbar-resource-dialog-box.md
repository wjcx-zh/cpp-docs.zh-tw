---
title: "新增工具列資源對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.newtoolbarresource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "新增工具列資源對話方塊"
ms.assetid: 52dd01ad-e748-4ab2-b3eb-59f5df990ca6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 新增工具列資源對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

\[新增工具列資源\] 對話方塊可讓您指定加入工具列資源的按鈕的寬度和長度。  預設值為 16 × 15 像素。  
  
 用來建立工具列的點陣圖最多可容許 2048 的寬度。  因此如果您將 \[**按鈕寬度**\] 設成 512，您只能有四個按鈕。  如果您將寬度設成 513，則只能有三個按鈕。  
  
 **按鈕寬度**  
 提供一個空間，讓您替經由點陣圖資源轉換成工具列資源所產生的工具列按鈕輸入寬度。  影像將剪裁為指定的寬度和長度，而色彩則調整為使用標準的工具列色彩 \(16 色\)。  
  
 **按鈕高度**  
 提供一個空間，讓您替經由點陣圖資源轉換成工具列資源所產生的工具列按鈕輸入長度。  影像將剪裁為指定的寬度和長度，而色彩則調整為使用標準的工具列色彩 \(16 色\)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 MFC 或 ATL  
  
## 請參閱  
 [Toolbar Button Properties](../mfc/toolbar-button-properties.md)   
 [Converting Bitmaps to Toolbars](../mfc/converting-bitmaps-to-toolbars.md)   
 [Toolbar Editor](../mfc/toolbar-editor.md)
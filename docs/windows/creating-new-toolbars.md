---
title: "Creating New Toolbars | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.toolbar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "toolbars [C++], creating"
  - "Toolbar editor, creating new toolbars"
  - "Insert Resource"
ms.assetid: 1b28264b-0718-4df8-9f65-979805d2efef
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creating New Toolbars
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要建立新的工具列  
  
1.  在 \[資源\] 檢視中，在 .rc 檔上按一下滑鼠右鍵，然後選擇捷徑功能表內的 \[加入資源\]   \(如果 .rc 檔中已經有工具列，您只要在 \[工具列\] 資料夾按一下滑鼠右鍵，然後選取捷徑功能表內的 \[插入工具列\]\)。  
  
     **請注意**：如果您的專案並未包含 .rc 檔案，請參閱[建立新的資源指令碼檔](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在 \[加入資源\] 對話方塊的 \[資源類型\] 清單中選取 \[工具列\]，接著按一下 \[新增\]。  
  
     如果有加號 \(\+\) 出現在 \[工具列\] 資源類型旁邊，即代表有工具列範本可供使用。  按一下加號可展開範本清單，請選取一個範本，然後按一下 \[新增\]。  
  
     \-或\-  
  
3.  [將現有點陣圖轉換為工具列](../mfc/converting-bitmaps-to-toolbars.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 MFC 或 ATL  
  
## 請參閱  
 [Toolbar Editor](../mfc/toolbar-editor.md)
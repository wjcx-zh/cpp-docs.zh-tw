---
title: "資源包含對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.resourceincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資源包含對話方塊"
  - "rc 檔案, 變更儲存區"
  - "符號標頭檔, 變更"
  - "編譯原始程式碼, 包含資源"
  - ".rc 檔案, 變更儲存區"
  - "符號標頭檔, 唯讀"
  - "符號, 符號標頭檔"
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資源包含對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 \[**資源包含**\] 對話方塊來修改環境的一般工作安排，此安排會儲存專案.rc 檔案中的所有資源，以及 Resource.h 中的所有[符號](../mfc/symbols-resource-identifiers.md)。  
  
 若要開啟 \[**資源包含**\] 對話方塊，請以滑鼠右鍵按一下 \[[資源檢視](../windows/resource-view-window.md)\] 中的 .rc 檔案，然後從捷徑功能表中選擇 \[**資源包含**\]。  
  
 **符號標頭檔**  
 可讓您變更標頭檔的名稱，您的資源的符號定義就是儲存在這個標頭檔中。  如需詳細資訊，請參閱[變更符號標頭檔的名稱](../windows/changing-the-names-of-symbol-header-files.md)。  
  
 **唯讀符號指示詞**  
 可讓您包含標頭檔，其中包含編輯工作階段期間不應該修改的符號。  例如，您可以包含數個專案之間共用的符號檔案。  您也可以包含 MFC.h 檔案。  如需詳細資訊，請參閱[包含共用 \(唯讀\) 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)。  
  
 **編譯時期指示詞**  
 可讓您包含從您的主要資源檔中資源個別建立和編輯的資源檔、包含編譯時期指示詞 \(例如，有條件地包含資源的編譯時期指示詞\)，或包含自訂格式的資源。  您也可以使用編譯時期指示詞方塊来包含標準 MFC 資源檔。  如需詳細資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。  
  
> [!NOTE]
>  這些文字方塊中的項目會出現 .rc 檔案中，分別以  `TEXTINCLUDE 1`、`TEXTINCLUDE 2` 和 `TEXTINCLUDE 3` 標示。  如需詳細資訊，請參閱[TN035：在 Visual C\+\+ 中使用多個資源檔和標頭檔](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。  
  
 一旦您已使用 \[**資源包含**\] 對話方塊變更了資源檔後，就需要關閉 .rc  檔案，然後再重新開啟，讓變更生效。  如需詳細資訊，請參閱[在編譯時期包含資源](../windows/how-to-include-resources-at-compile-time.md)。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [How to: Specify Include Directories for Resources](../windows/how-to-specify-include-directories-for-resources.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)
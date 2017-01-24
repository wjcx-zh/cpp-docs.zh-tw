---
title: "How to: Search for Symbols in Resources | Microsoft Docs"
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
helpviewer_keywords: 
  - "symbols, finding"
  - "resources [Visual Studio], searching for symbols"
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Search for Symbols in Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 若要尋找資源中的符號  
  
1.  從 \[**編輯**\] 功能表中，選擇 \[**尋找符號**\]。  
  
2.  在[尋找符號對話方塊](http://msdn.microsoft.com/zh-tw/63e93d9c-784f-418d-a76a-723da5ff5d96)的 \[**尋找目標**\] 方塊中，從下拉式清單中選取先前的搜尋字串，或輸入您想要尋找的快速鍵 \(例如，ID\_ACCEL1\)。  
  
    > [!TIP]
    >  若要使用[規則運算式](../Topic/Using%20Regular%20Expressions%20in%20Visual%20Studio.md)進行搜尋，您必須從 \[**編輯**\] 功能表中使用[在檔案中尋找命令](../Topic/Find%20Command.md)，而不是使用 \[**尋找符號**\] 命令。  若要啟用規則運算式，您必須已在[尋找對話方塊](http://msdn.microsoft.com/zh-tw/dad03582-4931-4893-83ba-84b37f5b1600)中選取 \[**使用：規則運算式**\] 核取方塊。  然後，您可以按一下 \[**尋找目標**\] 方塊右邊的向右箭號按鈕，以顯示規則搜尋運算式的清單。  當您從這個清單中選取運算式時，它會替代為 \[**尋找目標**\] 方塊中的搜尋文字。  
  
3.  選取任何 \[**尋找**\] 選項。  
  
4.  選擇 \[**尋找下一個**\]。  
  
    > [!NOTE]
    >  您無法在字串、快速鍵或二進位資源中搜尋符號。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **需求**  
  
 Win32  
  
## 請參閱  
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)
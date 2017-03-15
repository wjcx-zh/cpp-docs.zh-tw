---
title: "How to: Change the Language or Condition of a Resource While Copying | Microsoft Docs"
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
  - "vc.resvw.resource.changing"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Language property"
  - "condition property of resource"
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Change the Language or Condition of a Resource While Copying
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在資源中複製時，您可以變更其語言屬性或條件屬性，或兩者。  
  
-   資源的語言就是識別資源的語言。  這是由 [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) 使用，有助於識別您所尋找的資源。  \(不過，各語言的資源可能有與文字無關的差異，例如，只能在日文鍵盤上作用的快速鍵，或只適用於中文當地語系化組建的點陣圖等等\)。  
  
-   資源的條件是已定義的符號，用來識別使用此特定資源副本時的條件。  
  
 資源的語言和條件會顯示在 \[工作區\] 視窗中資源名稱後的括號中。  在此範例中，名為 IDD\_AboutBox 的資源使用芬蘭文為其語言，而其條件是 XX33。  
  
```  
IDD_AboutBox (Finnish – XX33)  
```  
  
### 複製現有的資源並變更其語言或條件  
  
1.  在 .rc 檔或 \[[資源檢視](../windows/resource-view-window.md)\] 視窗中，以滑鼠右鍵按一下您要複製的資源。  
  
2.  從快顯功能表選擇 \[**插入複本**\]。  
  
3.  在 \[**插入資源複本**\] 對話方塊中：  
  
    -   針對 \[**語言**\] 清單方塊，選取語言。  
  
    -   在 \[**條件**\] 方塊中輸入條件。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [How to: Copy Resources](../windows/how-to-copy-resources.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)
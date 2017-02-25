---
title: "Symbols: Resource Identifiers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.identifiers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbols, resource identifiers"
  - "symbols, creating"
  - "resource symbols"
  - "symbols, editing"
  - "resource editors, resource symbols"
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Symbols: Resource Identifiers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

符號是由兩部分所組成的資源識別碼 \(ID\)：對應至整數值 \(符號值\) 的文字字串 \(符號名稱\)。 例如：  
  
```  
IDC_EDITNAME = 5100  
```  
  
 符號名稱最常稱為識別項。  
  
 符號為您的原始程式碼中出現的資源和使用者介面物件，以及當您在資源編輯器中使用上述項目時，提供描述性參考。 您可以使用 \[資源符號\][](../windows/viewing-resource-symbols.md "Viewing Resource Symbols") 對話方塊，在一個方便的位置檢視及操作符號。  
  
 當您建立新的資源或資源物件時，\[資源編輯器\][](../mfc/resource-editors.md "Resource Editors") 會提供資源的預設名稱 \(例如 `IDC_RADIO1`\) 並為其指派值。 此名稱加值的定義會儲存在 Resource.h 檔案中。  
  
> [!NOTE]
>  當您將資源或資源物件從一個 .rc 檔複製到另一個檔案時，Visual C\+\+ 可能會變更已傳送資源的符號值，或符號名稱和值，以避免與現有檔案中的符號名稱或值相衝突。  
  
 當您的應用程式大小和複雜性提高時，其資源和符號數目也會增加。 追蹤分散於多個檔案的大量符號可能會很困難。 \[資源符號\][](../windows/resource-symbols-dialog-box.md "Resource Symbols Dialog Box") 對話方塊藉由提供集中工具來簡化符號管理，該工具可讓您：  
  
-   [檢視資源符號](../windows/viewing-resource-symbols.md)  
  
-   [建立新的符號](../windows/creating-new-symbols.md)  
  
-   [變更未指定的符號](../windows/changing-unassigned-symbols.md)  
  
-   [刪除未指定的符號](../windows/deleting-unassigned-symbols.md)  
  
-   [開啟指定符號的資源編輯器](../windows/opening-the-resource-editor-for-a-given-symbol.md)  
  
-   [變更符號或符號名稱 \(ID\)](../windows/changing-a-symbol-or-symbol-name-id.md)  
  
-   [變更符號的數值](../windows/changing-a-symbol-s-numeric-value.md)  
  
-   [變更符號標頭檔的名稱](../windows/changing-the-names-of-symbol-header-files.md)  
  
-   [包含共用 \(唯讀\) 或計算符號](../windows/including-shared-read-only-or-calculated-symbols.md)  
  
-   [檢視預先定義的符號 ID](../windows/predefined-symbol-ids.md)  
  
 如需將資源加入 Managed 專案的相關資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [How to: Search for Symbols in Resources](../windows/how-to-search-for-symbols-in-resources.md)   
 [Resource Editors](../mfc/resource-editors.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)
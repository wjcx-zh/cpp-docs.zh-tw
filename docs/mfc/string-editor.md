---
title: "String Editor | Microsoft Docs"
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
  - "vc.editors.string.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "String editor"
  - "string tables"
  - "string tables, String editor"
  - "string editing"
  - "string editing, string tables"
  - "resource editors, String editor"
  - "strings [C++], editing"
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

字串資料表是一種 Windows 資源，包含了識別碼、值與應用程式所有字串標題的清單。 例如，狀態列提示位於字串資料表中。  
  
 在開發應用程式時，您可能會有多個字串資料表，每種語言或條件各使用一個。 但可執行的模組只會有一個字串資料表。 若您將資料表置於不同的 DLL 中，則執行中的應用程式可以參考多個字串資料表。  
  
 字串資料表讓您很容易就能將應用程式當地語系化成不同的語言。 若所有字串都位於同一個字串資料表，您只需翻凙字串 \(及其他資源\)，就能當地語系化應用程式，無須變更原始程式碼。 這種方式相較於手動尋找及取代原始程式檔中的各種字串更為理想。  
  
 您可以使用字串編輯器：  
  
-   [搜尋一或多個字串](../mfc/finding-a-string.md)。  
  
-   快速[插入新項目](../mfc/adding-or-deleting-a-string.md)到字串資料表中。  
  
-   [在資源檔案之間移動字串](../mfc/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [使用就地編輯的識別碼、值與標題屬性](../mfc/changing-the-properties-of-a-string.md)，並立即檢視變更。  
  
-   [變更多個字串的標題屬性](../mfc/changing-the-caption-property-of-multiple-strings.md)  
  
-   [為字串加入格式或特殊字元](../mfc/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows 不允許建立空的字串資料表。 若建立的字串資料表中不含任何項目，將會在您儲存資源檔案時自動予以刪除。  
  
 如需將資源加入 Managed 專案中 \(亦即要使用 Common Language Runtime 專案\) 的資訊，請參閱 *.NET Framework 開發人員指南*中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。如需手動將資源檔加入 Managed 專案、存取資源、顯示靜態資源及指派資源字串給屬性的相關資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Resource Editors](../mfc/resource-editors.md)   
 [字串](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [關於字串](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)
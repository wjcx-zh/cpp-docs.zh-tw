---
title: "Symbol Name Restrictions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.symbol.restrictions.name"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "symbol names"
  - "symbols, names"
  - "restrictions, symbol names"
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Symbol Name Restrictions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

符號名稱限制如下所示：  
  
-   所有[符號](../mfc/symbols-resource-identifiers.md)在應用程式範圍內必須唯一。  這可避免標頭檔中出現衝突的符號定義。  
  
-   符號名稱的有效字元包括 A\-Z、a\-z、0\-9 和底線 \( \_ \)。  
  
-   符號名稱不能以數字開頭，而且僅限於 247 個字元。  
  
-   符號名稱不能包含空格。  
  
-   符號名稱不區分大小寫，但會保留第一個符號定義的大小寫。  定義符號的標頭檔是由資源編譯器\/編輯器和 C\+\+ 程式用來參考資源檔中定義的資源。  對於只有大小寫不同的兩個符號名稱，C\+\+ 程式會將其視為兩個不同的符號，而資源編譯器\/編輯器則會將這兩個名稱視為參考到單一符號。  
  
    > [!NOTE]
    >  如果您未遵循下列的標準符號名稱配置 \(ID\*\_\[keyword\]\)，而且您的符號名稱剛好與資源指令碼編譯器的已知關鍵字相同，則嘗試建置資源指令碼檔案會造成難以診斷的隨機錯誤產生。  若要避免這個問題，請遵守標準命名配置。  
  
 符號名稱具有描述性前置詞，指出它們所代表的資源或物件種類。  這些描述性前置詞的開頭為文字組合識別碼。  Microsoft Foundation Class 程式庫 \(MFC\) 使用下表所示的符號命名慣例。  
  
|類別|前置詞|使用|  
|--------|---------|--------|  
|資源|IDR\_ IDD\_ IDC\_ IDI\_ IDB\_|快速鍵或功能表 \(和相關或自訂資源\) 對話方塊游標圖示點陣圖|  
|功能表項目|ID\_|Menu item|  
|命令|ID\_|命令|  
|控制項和子視窗|IDC\_|控制|  
|字串|IDS\_|字串資料表中的字串|  
|MFC|AFX\_|保留給預先定義的 MFC 符號|  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源檔加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [Changing a Symbol or Symbol Name \(ID\)](../windows/changing-a-symbol-or-symbol-name-id.md)   
 [Symbol Value Restrictions](../windows/symbol-value-restrictions.md)   
 [Predefined Symbol IDs](../windows/predefined-symbol-ids.md)
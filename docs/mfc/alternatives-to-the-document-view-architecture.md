---
title: "文件/檢視架構的替代方案 | Microsoft Docs"
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
  - "CDocument 類別, 空間需求"
  - "文件, 應用程式不含"
  - "檢視, 應用程式不含"
ms.assetid: 2c22f352-a137-45ce-9971-c142173496fb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 文件/檢視架構的替代方案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 應用程式通常使用文件\/檢視架構處理資訊、檔案格式和資料的視覺呈現給使用者。  對於大部分的桌面應用程式，文件\/檢視架構是適當且有效率的應用程式架構。  這個結構是從檢視分隔資料，因此，在大部分情況下，簡化應用程式並減少多餘的程式碼。  
  
 不過，文件\/檢視架構為某些情況不適當。  請考量範例：  
  
-   如果您將 C\# 撰寫的應用程式視窗，您可能要將文件\/檢視支援前完成您的通訊埠加入至應用程式。  
  
-   如果您正在撰寫輕量型公用程式，您可能會發現您可以執行，而不使用文件\/檢視架構。  
  
-   如果原始程式碼與資料檢視已經混合資料管理，將程式碼移至文件\/檢視模型不值工作，因為您必須中斷連接兩個。  您可能想要留下程式碼。  
  
 若要建立不使用文件\/檢視架構的應用程式，請清除在 MFC 應用程式精靈的步驟 1 的 **Document\/View architecture support** 核取方塊。  請參閱 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md) 以取得詳細資訊。  
  
> [!NOTE]
>  MFC 應用程式精靈所產生的對話方塊架構的應用程式不使用文件\/檢視架構，，因此 **Document\/View architecture support** 核取方塊會停用，您還是可以選擇對話方塊應用程式類型。  
  
 Visual C\+\+ 精靈，以及來源和對話方塊編輯器，與產生的應用程式使用正它們會與其他精靈產生的應用程式。  應用程式可以支援工具列、捲軸和狀態列，而且有 \[**About**\] 方塊。  應用程式不會登錄任何文件樣板，因此它不會包含資料類別。  
  
 請注意產生的應用程式具有檢視類別， **CChildView**，衍生自 `CWnd`。  建立 MFC 和位置檢視類別的執行個體在應用程式中建立的框架視窗內。  因為它可簡化當地語系化和管理應用程式的內容，使用檢視視窗， MFC 仍然強制執行。  您可以將繪製程式碼加入至類別的 `OnPaint` 成員。  您的程式碼應該將捲軸加入檢視而不是加入至框架。  
  
 由於文件\/檢視架構的 MFC 提供了實作許多應用程式的基本功能，其在專案中找不到負責表示您負責實作應用程式許多重要功能:  
  
-   所提供由 MFC 應用程式精靈，您的應用程式功能表包含 `New` 和 `Exit` 命令只在**檔案**功能表。\( `New` 命令不會只針對 MDI 應用程式，而不是 SDI 應用程式支援不具有文件\/檢視支援\)。產生的功能表資源不支援 MRU \(最近使用的清單\)。  
  
-   您必須將處理函式和實作應用程式將支援的所有命令，包括 **Open** 和 **File** 在 \[**儲存**\] 功能表。  MFC 通常提供程式碼支援這些功能，不過，該支援緊密繫結至文件\/檢視架構。  
  
-   您的應用程式工具列，如果您要求一個工具列，將會是最小。  
  
 強烈建議您使用 MFC 應用程式精靈建立應用程式，而不使用文件\/檢視架構，，因為精靈保證的正確 MFC 結構。  不過，如果您必須避免使用精靈，這會略過的文件\/檢視架構幾種方法的程式碼:  
  
-   將文件當做一個未使用的附件並實作您的檢視類別的資料管理程式碼，如建議以上。  文件的額外負荷很低。  單一 [CDocument](../mfc/reference/cdocument-class.md) 物件本身產生較少的額外負荷，加上小負荷 **CDocument** 基底類別、 [CCmdTarget](../mfc/reference/ccmdtarget-class.md) 和 [CObject](../mfc/reference/cobject-class.md)。  兩個後者類別很小。  
  
     宣告在 **CDocument**:  
  
    -   兩個 `CString` 物件。  
  
    -   三個 **BOOL**的。  
  
    -   `CDocTemplate` 的指標。  
  
    -   建立 `CPtrList` 物件，包含文件的檢視清單。  
  
     此外，文件要求時間建立資料物件、其檢視物件、框架視窗與文件樣板物件。  
  
-   將文件和檢視為未使用的附件。  將資料管理和繪圖程式碼在框架視窗而不是檢視。  這個方法是 C 語言程式設計模型較接近。  
  
-   覆寫建立文件和檢視中排除建立它們 MFC 架構的一部分。  此文件創造處理序一開始會呼叫 `CWinApp::AddDocTemplate` 。  從您的應用程式類別的 `InitInstance` 成員函式排除該呼叫，而且，相反地，會在 `InitInstance` 的框架視窗。  將資料管理程式碼在框架視窗類別。  文件\/檢視建立程序在 [文件\/檢視建立](../mfc/document-view-creation.md)中說明。  這是更多工作並需要架構的更深入了解，不過它可以讓您完全文件\/檢視額外負荷。  
  
 這篇文章 [MFC:使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md) 將文件\/檢視選取的特定執行個體在資料庫應用程式中。  
  
## 請參閱  
 [文件\/檢視架構](../mfc/document-view-architecture.md)
---
title: "建立檔案總管樣式的 MFC 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfcexplorer.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "瀏覽器, 檔案總管樣式應用程式"
  - "檔案總管樣式應用程式, 建立"
  - "MFC 應用程式, 檔案總管樣式"
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立檔案總管樣式的 MFC 應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

許多 Windows 應用為檔案總管使用 User Interface \(UI\)。  例如，時，啟動檔案總管中看到與分割工作區的一個垂直分隔列的應用程式。  工作區左邊提供巡覽和瀏覽功能，而工作區的右邊則顯示左窗格選項的相關詳細資訊。  使用者在左窗格按一下某項目時，應用程式會重新填入右窗格。  在 MDI 應用程式中，您可使用 \[**檢視**\] 功能表上的命令，變更右窗格內要顯示的詳細資訊量 \(在 SDI 或多重最上層文件應用程式中，僅可使用工具列按鈕變更詳細資訊\)。  
  
 窗格的內容依應用程式而定。  在檔案系統瀏覽器中，左窗格顯示出目錄、電腦或電腦群組的階層檢視，而右窗格則顯示資料夾、個別檔案或電腦，以及其相關資訊。  內容不一定是檔案。  他們可以是電子郵件訊息、錯誤報告或資料庫的其他項目。  
  
 精靈可為您建立下列類別：  
  
-   **CLeftView** 類別定義工作區的左窗格。  固定衍生自 [CTreeView](../../mfc/reference/ctreeview-class.md)。  
  
-   C*ProjName*View 類別定義工作區的右窗格。  在預設情況下，是從 [CListView](../../mfc/reference/clistview-class.md) 衍生而來，但是也可以根據精靈中[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁的 \[基底類別\] 清單內所指定的類別，成為另一種檢視類型。  
  
 產生的應用程式可包含單一文件介面 \(SDI\)、多重文件介面 \(MDI\)，或者多重最上層文件架構。  應用程式所建立的每個框架視窗 \(Frame Window\)，皆使用 [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) 垂直分隔。  為此種應用程式撰寫程式碼，與為使用分隔器 \(Splitter\) 的一般 MFC 應用程式相似；不同的是，此類型的應用程式在各個分隔窗格中，擁有各自的控制項檢視。  
  
 如果您在右窗格內使用預設的清單檢視，精靈會建立額外的功能表選項 \(僅限於 MDI 應用程式中\) 和工具列按鈕，以便切換檢視樣式為大圖示、小圖示、清單或詳細資料模式。  
  
### 開始建立檔案總管樣式的 MFC 可執行檔  
  
1.  請依照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)的指示進行操作。  
  
2.  在 MFC 應用程式精靈的 [應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md) 頁面中，選取 \[**檔案總管**\] 專案樣式。  
  
3.  在精靈的其他頁面上，視您的需要設定其他選項。  
  
4.  按一下 \[完成\] 以產生基本架構應用程式。  
  
 如需詳細資訊，請參閱：  
  
-   [多重文件類型、檢視和框架視窗](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [應用程式設計選擇](../../mfc/application-design-choices.md)  
  
## 請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [建立 Web 瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [建立表單架構的 MFC 應用程式](../../mfc/reference/creating-a-forms-based-mfc-application.md)
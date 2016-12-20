---
title: "建立表單架構的 MFC 應用程式 | Microsoft Docs"
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
  - "vc.appwiz.mfcforms.project"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "應用程式 [MFC], 表單架構"
  - "表單架構應用程式"
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立表單架構的 MFC 應用程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表單是包含控制項的對話方塊，可供使用者存取並且盡可能地變更資料。  您所開發的應用程式，最好能夠讓使用者從各種表單選項中進行選取。  一般而言，表單架構應用程式可以讓使用者透過點選\[**檔案**\] 功能表中的 \[**新增**\] 來存取表單。  對話方塊架構應用程式並未在 \[檔案\] 功能表內提供 \[**新增**\] 選項，但同樣屬於表單架構應用程式。  
  
 單一文件介面 \(SDI\) 表單架構應用程式，一次僅容許某特定表單的單一執行個體 \(Instance\) 執行。  藉由在 \[檔案\] 功能表內的 \[**新增**\] 選項中選取新表單，即可從 SDI 表單架構應用程式中同時執行多個表單。  
  
 如果您建立多重文件介面 \(MDI\) 表單架構應用程式，則應用程式可支援相同表單的多個執行個體。  
  
 如果您建立的應用程式中，包含多重最上層文件支援，則桌面是文件的隱含上層，且文件的框架並未受限於應用程式的工作區 \(Client Area\)。  您可以開啟多個文件的執行個體，每個執行個體皆有其個別的框架、功能表以及工作列圖示。  您可分別關閉文件的後續執行個體，但如果您從初始執行個體的 \[**檔案**\] 功能表中選取 \[`Exit` \] 選項，則應用程式會關閉所有執行個體。  
  
 SDI、MDI 和多重最上層文件應用程式皆為表單架構，並使用文件 \/ 檢視架構。  
  
 根據定義而言，所有對話方塊架構應用程式皆以表單為基礎。  對話方塊架構應用程式不使用文件 \/ 檢視架構，因此您必須為個人的額外表單，在方法的建立和存取上做管理。  
  
 表單架構應用程式的基底類別 \(Base Class\) 是 [CFormView](../../mfc/reference/cformview-class.md)。  如果應用程式可支援資料庫，則您也可以選取從 `CFormView` 衍生而來的任意類別。  表單是從 `CFormView`，或者從繼承自 `CFormView` 的任意類別所衍生的任意視窗。  
  
 即使您使用 [CView](../../mfc/reference/cview-class.md) 這樣的基底類別，您也可以透過[加入 MFC 類別](../../mfc/reference/adding-an-mfc-class.md) \(衍生自 `CFormView` 的類別\)，並於 [MFC 類別精靈](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md)中核取 \[產生 DocTemplate 資源\] 核取方塊，來將應用程式變更為表單架構。  
  
 精靈完成之後，專案隨即開啟。如果您選取 `CFormView` \(或繼承自 `CFormView` 的類別\) 做為基底類別，或者您建立的是對話方塊架構應用程式，Visual C\+\+ 會開啟對話方塊編輯器。  此時，您已經準備好設計第一個表單。  
  
### 若要開始建立表單架構的 MFC 可執行檔  
  
1.  請依照[建立 MFC 應用程式](../../mfc/reference/creating-an-mfc-application.md)的指示進行操作。  
  
2.  在 MFC 應用程式精靈的[應用程式類型](../../mfc/reference/application-type-mfc-application-wizard.md)頁面中，選取 \[支援文件\/檢視架構\] 核取方塊。  
  
3.  選取 \[單一文件\]、\[多份文件\] 或 \[多重最上層文件\]。  
  
    > [!NOTE]
    >  如果您選擇 SDI、MDI 或多重最上層文件介面應用程式，則在精靈的[產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面中，`CView` 為預設之應用程式檢視的基底類別。  若要建立表單架構應用程式，您必須選取 `CFormView` 做為應用程式檢視的基底類別。  請注意，精靈不提供表單架構應用程式的列印支援。  
  
4.  視您的需要，在精靈的其他頁面上設定專案選項。  
  
5.  按一下 \[完成\] 以產生基本架構應用程式。  
  
 如需詳細資訊，請參閱：  
  
-   [衍生的檢視類別](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [文件\/檢視架構的替代方案](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [應用程式設計選擇](../../mfc/application-design-choices.md)  
  
## 請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [表單檢視](../../mfc/form-views-mfc.md)   
 [建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [建立 Web 瀏覽器樣式的 MFC 應用程式](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)
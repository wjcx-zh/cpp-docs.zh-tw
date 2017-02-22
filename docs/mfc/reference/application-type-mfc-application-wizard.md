---
title: "MFC 應用程式精靈、應用程式類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.apptype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "靜態程式庫, MFC"
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MFC 應用程式精靈、應用程式類型
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)中的這個頁面，即可設計新的 MFC 應用程式，並在其中加入基本功能。  
  
 **應用程式類型**  
 指定您要在應用程式中建立的文件支援類型。  您所選取的應用程式類型，可決定應用程式可用的使用者介面選項。  如需詳細資訊，請參閱[MFC 應用程式精靈、使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)。  
  
 如需文件類型的詳細資訊，請參閱：  
  
-   [SDI 和 MDI](../../mfc/sdi-and-mdi.md)  
  
-   [框架視窗](../../mfc/frame-windows.md)  
  
-   [框架視窗類別](../../mfc/frame-window-classes.md)  
  
-   [文件、檢視和架構](../../mfc/documents-views-and-the-framework.md)  
  
-   [對話方塊](../../mfc/dialog-boxes.md)  
  
|選項|說明|  
|--------|--------|  
|**單一文件介面**|為應用程式建立單一文件介面 \(SDI\) 架構，其檢視類別是以 [CView Class](../../mfc/reference/cview-class.md)為基礎。  您可於精靈的 [MFC 應用程式精靈、產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面中，變更檢視的基底類別。  例如，若要建立表單架構應用程式，請使用 [CFormView Class](../../mfc/reference/cformview-class.md)做為檢視類別。<br /><br /> 在這種應用程式類型中，文件的框架視窗只能保留一份文件。|  
|**多重文件介面**|為應用程式建立多重文件介面 \(MDI\) 架構，其檢視類別是以 `CView` 為基礎。  您可於精靈的**產生的類別**頁面中，變更檢視的基底類別。  例如，若要建立表單架構應用程式，請使用 `CFormView` 做為檢視類別。<br /><br /> 在這種應用程式類型中，文件的框架視窗可保留多個子視窗。|  
|**索引標籤式文件**|將每份文件置於個別的索引標籤上。|  
|**對話方塊架構**|為應用程式建立對話方塊型架構，其對話方塊類別是以 `CDialog` 為基礎 \(若要建立 HTML 對話方塊，請選取 \[**使用 HTML 對話方塊**\]\)。|  
|**使用 HTML 對話方塊\(I\)**|限對話方塊應用程式使用。  從 [CDHtmlDialog Class](../../mfc/reference/cdhtmldialog-class.md)而非 [CDialog Class](../../mfc/reference/cdialog-class.md)衍生對話方塊類別。  如果您核取這個方塊，`CDHtmlDialog` 會在精靈之 [MFC 應用程式精靈、產生的類別](../../mfc/reference/generated-classes-mfc-application-wizard.md)頁面的 \[**基底類別**\] 方塊內列出。<br /><br /> `CDHtmlDialog` 衍生的對話方塊會顯示以 HTML 為基礎的對話方塊、與 HTML 控制項交換資料，以及處理 HTML 事件。|  
|**多重最上層文件\(T\)**|為應用程式建立多重最上層架構，其檢視類別是以 `CView` 為基礎。<br /><br /> 在這種應用程式類型中，使用者若按一下 \[**檔案**\] 功能表上的 \[**開新檔案**\] \(或 \[**新增框架**\]\)，應用程式會建立父代為隱含桌面的視窗。  新文件框架隨即顯示於工作列中，且不限於應用程式視窗的用戶端區域中。|  
  
 **文件\/檢視架構支援**  
 使用 [CDocument Class](../../mfc/reference/cdocument-class.md)和 [CView Class](../../mfc/reference/cview-class.md) \(預設\)，指定是否要將文件\/檢視架構包括在應用程式中。  如果正要移植非 MFC 應用程式，或者準備縮減已編譯過的可執行檔大小，請清除這個核取方塊。  根據預設，不具有文件\/檢視架構的應用程式是衍生自 [CWinApp Class](../../mfc/reference/cwinapp-class.md)，而且不包含從磁碟檔案中開啟文件的 MFC 支援。  
  
 **資源語言**  
 設定資源的語言。  清單中顯示出系統上可用的語言，即 Visual Studio 的安裝結果。  如果您要選取系統語言之外的其他語言，則必須安裝該語言的適當範本資料夾。  如需安裝 \[**資源語言**\] 預設清單以外之語言資源的詳細資訊，請參閱[其他語言的精靈支援](../../ide/wizard-support-for-other-languages.md)。  
  
 您所選取的語言會反應於精靈之 [MFC 應用程式精靈、文件樣板字串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)頁面的 \[**當地語系化字串**\] 選項中。  
  
 **使用 Unicode 程式庫**  
 指定使用 Unicode 版本或非 Unicode 版本的 MFC 程式庫。  
  
 **專案樣式**  
 表示應用程式是否有標準 MFC、檔案總管、Visual Studio 或 Office 架構和顯示。  如需詳細資訊，請參閱[建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)。  
  
|選項|說明|  
|--------|--------|  
|**MFC 標準**|提供標準的 MFC 應用程式架構。|  
|**檔案總管**|實作檔案與檔案總管類似的應用程式使用左窗格是 [CTreeView Class](../../mfc/reference/ctreeview-class.md) 的分隔視窗，而右窗格是 [CListView Class](../../mfc/reference/clistview-class.md)。|  
|**Visual Studio**|實作如 Visual Studio 的應用程式，其中包含四個衍生自 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)的可停駐窗格 \(\[**檔案檢視**\]、\[**類別檢視**\]、\[**屬性**\] 和 \[**輸出**\]\)，以及一個衍生自 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md) \(預設\) 的主框架視窗。|  
|**Office**|實作如 Office 的應用程式，其中包含一個衍生自 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)的功能區、衍生自 [CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)的 Outlook 功能區、衍生自 [CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)的標題列，以及衍生自 [CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)的主窗格。|  
  
 **視覺化樣式和色彩**  
 決定應用程式的視覺化樣式。  下列為可用的選項：  
  
-   **Windows 原有\/預設**  
  
-   **Office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 \(藍色佈景主題\)**  
  
-   **Office 2007 \(黑色佈景主題\)**  
  
-   **Office 2007 \(銀色佈景主題\)**  
  
-   **Office 2007 \(青色佈景主題\)**  
  
 **啟用視覺化樣式切換**  
 指定使用者是否可以在執行階段變更應用程式的視覺化樣式，通常這是藉由選取功能表或功能區上適當的視覺化樣式來達成。  
  
 **MFC 的使用**  
 指定如何連結 MFC 程式庫。  MFC 預設是連結為共用 DLL。  
  
|選項|說明|  
|--------|--------|  
|**使用 MFC 的共用 DLL\(U\)**|將 MFC 程式庫連結至應用程式，做為共用 DLL。  應用程式會在執行階段時呼叫 MFC 程式庫。  如果應用程式是由使用 MFC 程式庫的多個可執行檔所組成，則本選項會降低其磁碟與記憶體需求。  Win32 和 MFC 應用程式都可以在 DLL 中呼叫函式 \(預設\)。|  
|**使用 MFC 的靜態程式庫\(E\)**|於建置時期將應用程式連結至 MFC 靜態程式庫。|  
  
## 請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [為 Visual C\+\+ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)
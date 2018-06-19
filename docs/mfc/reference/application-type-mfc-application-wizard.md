---
title: MFC 應用程式精靈、 應用程式類型 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.apptype
dev_langs:
- C++
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5708e823c57ecdb8470a398c4192cba1a5b6e411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353435"
---
# <a name="application-type-mfc-application-wizard"></a>MFC 應用程式精靈、應用程式類型
使用此頁面的[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)來設計並將新的 MFC 應用程式的基本功能。  
  
 **應用程式類型**  
 指定您想要在您的應用程式中建立的文件支援的類型。 您選取的應用程式類型會決定可供您的應用程式的使用者介面選項。 請參閱[MFC 應用程式精靈、 使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)如需詳細資訊。  
  
 如需類型的文件的詳細資訊，請參閱：  
  
-   [SDI 和 MDI](../../mfc/sdi-and-mdi.md)  
  
-   [框架視窗](../../mfc/frame-windows.md)  
  
-   [框架視窗類別](../../mfc/frame-window-classes.md)  
  
-   [文件、檢視和架構](../../mfc/documents-views-and-the-framework.md)  
  
-   [對話方塊](../../mfc/dialog-boxes.md)  
  
|選項|描述|  
|------------|-----------------|  
|**單一文件**|建立單一文件介面 (SDI) 架構應用程式，其中的檢視類別根據[CView 類別](../../mfc/reference/cview-class.md)。 您可以變更檢視中的基底類別[產生的類別，MFC 應用程式精靈](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。 若要建立表單架構應用程式，例如，使用[CFormView 類別](../../mfc/reference/cformview-class.md)檢視類別。<br /><br /> 在這種應用程式的文件框架視窗可以保存只能有一個文件。|  
|**多個文件**|建立您的應用程式，其中的檢視類別根據多個文件介面 (MDI) 架構`CView`。 您可以變更檢視中的基底類別**產生的類別**精靈頁面。 若要建立表單架構應用程式，例如，使用`CFormView`檢視類別。<br /><br /> 在這種應用程式的文件框架視窗可以保存多個子 windows。|  
|**索引標籤式文件**|每份文件放置於另一個索引標籤。|  
|**對話方塊架構**|建立您的應用程式的對話方塊類別為基礎，對話方塊架構架構`CDialog`。 (若要建立的 [HTML] 對話方塊，選取方塊**對話方塊使用 HTML**。)|  
|**使用 HTML 對話方塊**|對話方塊方塊僅為應用程式。 衍生對話方塊類別從[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)而不是[CDialog 類別](../../mfc/reference/cdialog-class.md)。 如果您核取此方塊，`CDHtmlDialog`會列在**基底類別**方塊中[產生的類別，MFC 應用程式精靈](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。<br /><br /> A `CDHtmlDialog`-衍生的對話方塊顯示 HTML 為基礎的對話方塊，請使用 HTML 的交換資料控制項和處理 HTML 事件。|  
|**多個最上層文件**|建立您的應用程式，其中的檢視類別根據多個最上層架構`CView`。<br /><br /> 在這種類型的應用程式，當使用者按一下**新增**(或**新框架**) 上**檔案**功能表上，應用程式建立的父代為隱含桌面視窗。 新的文件框架出現在工作列中，不受限於應用程式視窗的工作區。|  
  
 **文件/檢視架構支援**  
 指定是否要包含在應用程式中的文件/檢視架構使用[CDocument 類別](../../mfc/reference/cdocument-class.md)和[CView 類別](../../mfc/reference/cview-class.md)（預設值）。 如果您要移植非 MFC 應用程式，或如果您想要減少編譯可執行檔的大小，請清除此核取方塊。 根據預設，不具有文件/檢視架構的應用程式衍生自[CWinApp 類別](../../mfc/reference/cwinapp-class.md)，而且不包含 MFC 支援的磁碟檔案從開啟的文件。  
  
 **資源語言**  
 設定資源的語言。 清單會顯示可用的語言在您系統上，為已安裝 Visual studio。 如果您想要選取您的系統語言以外之語言，必須已安裝該語言的適當的範本資料夾。 如需有關安裝與使用中的預設值不同的語言資源**資源語言**清單中，請參閱[其他語言的精靈支援](../../ide/wizard-support-for-other-languages.md)。  
  
 您選取的語言會反映在**當地語系化字串**選項[文件樣板字串、 MFC 應用程式精靈](../../mfc/reference/document-template-strings-mfc-application-wizard.md)精靈頁面。  
  
 **使用 Unicode 程式庫**  
 指定是否要使用 MFC 程式庫的 Unicode 或非 Unicode 版本。  
  
 **專案樣式**  
 指出您的應用程式是否有標準 MFC、 檔案總管 中，Visual Studio 中，或 Office 架構和顯示。 如需詳細資訊，請參閱[建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)。  
  
|選項|描述|  
|------------|-----------------|  
|**MFC 的標準**|提供標準的 MFC 應用程式架構。|  
|**檔案總管**|實作類似檔案總管的應用程式的檔案使用所在的左的窗格的分隔視窗[CTreeView 類別](../../mfc/reference/ctreeview-class.md)而右窗格是[CListView 類別](../../mfc/reference/clistview-class.md)。|  
|**Visual Studio**|實作包含四個可停駐窗格的 Visual Studio 類似的應用程式 (**檔案檢視**，**類別檢視**，**屬性**，和**輸出**)，都是衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)和主框架視窗是衍生自[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)（預設值）。|  
|**Office**|實作類似 Office 的應用程式，其中包含衍生自的功能區[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)，衍生自 outlook 功能區[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)，衍生自的標題列[CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)，以及衍生自的主要畫面格[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。|  
  
 **視覺化樣式和色彩**  
 判斷應用程式的視覺化樣式。 有下列選項可供使用：  
  
-   **Windows 原生/預設值**  
  
-   **office 2003**  
  
-   **Visual Studio 2005**  
  
-   **Office 2007 （藍色主題）**  
  
-   **Office 2007 （黑色主題）**  
  
-   **Office 2007 （銀色主題）**  
  
-   **Office 2007 （青色主題）**  
  
 **啟用視覺化樣式切換**  
 指定使用者是否可以變更之視覺樣式的應用程式在執行階段，通常從功能表或功能區中選取適當的視覺化樣式。  
  
 **MFC 的使用**  
 指定如何連結至 MFC 程式庫。 根據預設，MFC 會為共用的 DLL 連結。  
  
|選項|描述|  
|------------|-----------------|  
|**使用 MFC 共用 dll**|MFC 程式庫共用的 dll 的應用程式的連結。 應用程式會呼叫 MFC 程式庫，在執行階段。 這個選項可以減少使用的 MFC 程式庫的多個可執行檔所組成的應用程式的磁碟和記憶體需求。 Win32 和 MFC 應用程式可以呼叫您的 DLL （預設值） 中的函式|  
|**使用 MFC 的靜態程式庫**|連結至 MFC 靜態程式庫應用程式在建置階段。|  
  
## <a name="see-also"></a>另請參閱  
 [MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)   
 [為 Visual C++ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)


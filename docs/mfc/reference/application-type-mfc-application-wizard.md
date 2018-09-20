---
title: 應用程式類型、 MFC 應用程式精靈 |Microsoft Docs
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
ms.openlocfilehash: e7d27245e06350a9174699fc20246d5e8997795d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434371"
---
# <a name="application-type-mfc-application-wizard"></a>MFC 應用程式精靈、應用程式類型

使用此頁面[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)設計，並加入新的 MFC 應用程式的基本功能。

- **應用程式類型**

   指定您想要在您的應用程式中建立的文件支援的類型。 您選取的應用程式類型會決定可供您的應用程式的使用者介面選項。 請參閱[MFC 應用程式精靈、 使用者介面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)如需詳細資訊。

   如需詳細的文件類型的詳細資訊，請參閱：

   - [SDI 和 MDI](../../mfc/sdi-and-mdi.md)

   - [框架視窗](../../mfc/frame-windows.md)

   - [框架視窗類別](../../mfc/frame-window-classes.md)

   - [文件、檢視和架構](../../mfc/documents-views-and-the-framework.md)

   - [對話方塊](../../mfc/dialog-boxes.md)

   |選項|描述|
   |------------|-----------------|
   |**單一文件**|建立您的應用程式，其中的檢視類別為基礎的單一文件介面 (SDI) 架構[CView 類別](../../mfc/reference/cview-class.md)。 您可以變更檢視中的基底類別[產生的類別，MFC 應用程式精靈](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。 若要建立表單架構應用程式，例如，使用[CFormView 類別](../../mfc/reference/cformview-class.md)檢視類別。<br /><br /> 在這種應用程式，文件的框架視窗可以保留只能有一個文件。|
   |**多個文件**|建立您的應用程式，其中的檢視類別根據多個文件介面 (MDI) 架構`CView`。 您可以變更檢視中的基底類別**產生的類別**精靈頁面。 若要建立表單架構應用程式，例如，使用`CFormView`檢視類別。<br /><br /> 在這種應用程式中的文件框架視窗可保留多個子視窗。|
   |**索引標籤式文件**|置於另一個索引標籤中的每份文件。|
   |**對話方塊架構**|建立對話方塊架構的架構，其中的對話方塊類別為基礎的應用程式`CDialog`。 (若要建立的 HTML 對話方塊，選取 方塊**使用 HTML 對話方塊**。)|
   |**使用 HTML 對話方塊**|對話方塊方塊僅為應用程式。 衍生的對話方塊類別[CDHtmlDialog 類別](../../mfc/reference/cdhtmldialog-class.md)而不是[CDialog 類別](../../mfc/reference/cdialog-class.md)。 如果您核取此方塊中，`CDHtmlDialog`中列為**基底類別**方塊中[產生的類別，MFC 應用程式精靈](../../mfc/reference/generated-classes-mfc-application-wizard.md)精靈頁面。<br /><br /> A `CDHtmlDialog`-衍生的對話方塊會顯示以 HTML 為基礎的對話方塊中，交換資料，與 HTML 控制項和處理 HTML 事件。|
   |**多個最上層的文件**|建立您的應用程式，其中的檢視類別為基礎的多個頂層架構`CView`。<br /><br /> 在這種應用程式，當使用者按一下**的新**(或**新的框架**) 上**檔案** 功能表中，應用程式建立其父代會以隱含方式在桌面上的視窗。 新的文件框架出現在工作列中，並不受限於應用程式視窗的工作區。|

- **文件/檢視架構支援**

   指定是否要包含在您的應用程式中的文件/檢視架構，使用[CDocument 類別](../../mfc/reference/cdocument-class.md)並[CView 類別](../../mfc/reference/cview-class.md)（預設值）。 如果您要移植的非 MFC 應用程式，或如果您想要減少編譯可執行檔的大小，請清除此核取方塊。 根據預設，不具有文件/檢視架構的應用程式衍生自[CWinApp 類別](../../mfc/reference/cwinapp-class.md)，而且不包含從磁碟檔案中開啟文件的 MFC 支援。

- **資源語言**

   設定資源的語言。 清單會顯示可用的語言在您的系統，由 Visual Studio 安裝。 如果您想要選取您的系統語言以外的語言，必須已安裝該語言的適當的範本資料夾。 如需有關安裝與使用中的預設值不同的語言資源**資源語言**清單中，請參閱[其他語言的精靈支援](../../ide/wizard-support-for-other-languages.md)。

   您選取的語言會反映在**當地語系化字串**選項[文件樣板字串、 MFC 應用程式精靈](../../mfc/reference/document-template-strings-mfc-application-wizard.md)精靈頁面。

- **使用 Unicode 程式庫**

   指定是否要使用的 Unicode 或非 Unicode 版本的 MFC 程式庫。

- **專案樣式**

   指出您的應用程式是否有標準 MFC、 檔案總管 中，Visual Studio 中，或 Office 架構與顯示。 如需詳細資訊，請參閱 <<c0> [ 建立檔案總管樣式的 MFC 應用程式](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)。

   |選項|描述|
   |------------|-----------------|
   |**MFC 的標準**|提供標準的 MFC 應用程式架構。|
   |**檔案總管**|實作檔案總管類似的應用程式使用分隔器視窗的左的窗格的所在[CTreeView 類別](../../mfc/reference/ctreeview-class.md)，而右邊的窗格是[CListView 類別](../../mfc/reference/clistview-class.md)。|
   |**Visual Studio**|實作包含四個可停駐窗格的 Visual Studio 類似的應用程式 (**檔案檢視**，**類別檢視**，**屬性**，和**輸出**)，衍生自[CDockablePane 類別](../../mfc/reference/cdockablepane-class.md)衍生自一個主框架視窗[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)（預設值）。|
   |**Office**|實作類似 Office 的應用程式，其中包含一個功能區，衍生自[CMFCRibbonBar 類別](../../mfc/reference/cmfcribbonbar-class.md)，Outlook 功能區是衍生自[CMFCOutlookBar 類別](../../mfc/reference/cmfcoutlookbar-class.md)，衍生自的標題列[CMFCCaptionBar 類別](../../mfc/reference/cmfccaptionbar-class.md)，以及衍生自的主要畫面格[CMDIFrameWndEx 類別](../../mfc/reference/cmdiframewndex-class.md)。|

- **視覺化樣式和色彩**

   判斷應用程式的視覺化樣式。 有下列選項可供使用：

   - **Windows 原生/預設值**

   - **Office 2003**

   - **Visual Studio 2005**

   - **Office 2007 （藍色佈景主題）**

   - **Office 2007 （黑色佈景主題）**

   - **Office 2007 （銀色佈景主題）**

   - **Office 2007 （青色佈景主題）**

- **啟用視覺化樣式切換**

   指定使用者是否可以變更之視覺樣式的應用程式在執行階段，通常從功能表或功能區中選取適當的視覺化樣式。

- **MFC 用途**

   指定如何連結至 MFC 程式庫。 根據預設，MFC 會做為共用的 DLL 連結。

   |選項|描述|
   |------------|-----------------|
   |**使用 MFC 的共用 DLL**|MFC 程式庫共用的 DLL 的應用程式的連結。 應用程式會呼叫 MFC 程式庫，在執行階段。 此選項會降低使用 MFC 程式庫的多個可執行檔所組成的應用程式的磁碟和記憶體需求。 Win32 和 MFC 應用程式可以呼叫您的 DLL （預設值） 中的函式|
   |**使用 MFC 的靜態程式庫**|連結至 MFC 靜態程式庫應用程式在建置階段。|

## <a name="see-also"></a>另請參閱

[MFC 應用程式精靈](../../mfc/reference/mfc-application-wizard.md)<br/>
[為 Visual C++ 專案建立的檔案類型](../../ide/file-types-created-for-visual-cpp-projects.md)


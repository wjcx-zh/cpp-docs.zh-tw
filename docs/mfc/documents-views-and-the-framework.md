---
title: 文件、檢視和架構
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 799035976ea55988a635f7dc9b667e87c48d8f7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273500"
---
# <a name="documents-views-and-the-framework"></a>文件、檢視和架構

MFC 架構的核心是文件和檢視的概念。 文件是一種在編輯工作階段與使用者進行互動的資料物件。 它由**新增**或是**開啟**命令**檔案**功能表，通常會儲存在檔案中。 (標準 MFC 文件，衍生自類別`CDocument`，不同於主動式文件和 OLE 複合文件。)檢視是一種使用者與文件互動的視窗物件。

執行中應用程式的主要物件如下：

- 一個或多個文件。

   您的文件類別 (衍生自[CDocument](../mfc/reference/cdocument-class.md)) 指定您的應用程式資料。

   如果您想要 OLE 功能，在您的應用程式中，衍生您的文件類別，從[COleDocument](../mfc/reference/coledocument-class.md)或其中一個衍生的類別，根據您所需要的功能的類型。

- 一個或多個檢視。

   您的檢視類別 (衍生自[CView](../mfc/reference/cview-class.md)) 是使用者的 「 視窗的資料。 」 檢視類別可控制使用者如何查看文件的資料以及與其互動。 在某些情況下，您可能想要讓文件擁有多個資料檢視。

   如果您需要捲動，則衍生自[CScrollView](../mfc/reference/cscrollview-class.md)。 如果您的檢視具有在對話方塊範本資源中配置使用者介面，則衍生自[CFormView](../mfc/reference/cformview-class.md)。 針對簡單的文字資料，使用或衍生自[CEditView](../mfc/reference/ceditview-class.md)。 對於以 form 為基礎的資料存取應用程式，例如資料輸入程式，衍生自[CRecordView](../mfc/reference/crecordview-class.md) （適用於 ODBC)。 可用的類別還有[CTreeView](../mfc/reference/ctreeview-class.md)， [CListView](../mfc/reference/clistview-class.md)，並[CRichEditView](../mfc/reference/cricheditview-class.md)。

- 框架視窗

   檢視會顯示在「文件框架視窗」內部。 在 SDI 應用程式中，文件框架視窗也是應用程式的「主框架視窗」。 在 MDI 應用程式中，文件視窗是會顯示在主框架視窗內的子視窗。 您衍生的主框架視窗類別會指定樣式和包含檢視之框架視窗的其他特性。 如果您需要自訂框架視窗，衍生自[CFrameWnd](../mfc/reference/cframewnd-class.md)以自訂 SDI 應用程式的文件框架視窗。 衍生自[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)自訂 MDI 應用程式的主框架視窗。 也衍生的類別[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)來自訂每一種不同的應用程式所支援的 MDI 文件框架視窗。

- 一個或多個文件範本

   文件範本會協調文件、檢視和框架視窗的建立。 特定的文件樣板類別，衍生自類別[CDocTemplate](../mfc/reference/cdoctemplate-class.md)、 建立和管理所有開啟的文件的一種類型。 支援多種文件類型的應用程式擁有多個文件範本。 使用類別[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI 應用程式，或使用類別[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) MDI 應用程式。

- 應用程式物件

   您的應用程式類別 (衍生自[CWinApp](../mfc/reference/cwinapp-class.md)) 控制所有上述物件，並指定應用程式的行為，例如初始化和清除。 應用程式唯一的應用程式物件會建立及管理應用程式所支援任何資料類型的文件範本。

- 執行緒物件

   如果您的應用程式建立個別的執行緒執行的 — 例如，若要在背景執行計算，您將使用衍生自類別[CWinThread](../mfc/reference/cwinthread-class.md)。 [CWinApp](../mfc/reference/cwinapp-class.md)本身衍生自`CWinThread`並代表應用程式中的主執行緒的執行 （或主要處理序）。 您也可以在次要執行緒中使用 MFC。

在執行中的應用程式中，這些物件會一起回應使用者動作，並透過命令和其他訊息繫結程序在一起。 單一應用程式物件會管理一個或多個文件範本。 每個文件範本會建立和管理一個或多個文件 (根據應用程式為 SDI 還是 MDI 而定)。 使用者透過框架視窗中的檢視來檢視和操作文件。 下圖顯示 SDI 應用程式中這些物件之間的關聯性。

![在執行中 SDI 應用程式中的物件](../mfc/media/vc386v1.gif "執行中 SDI 應用程式中的物件") <br/>
執行中 SDI 應用程式內的物件

這一系列的其他文章說明架構工具、MFC 應用程式精靈和資源編輯器如何建立這些物件、它們如何一起運作，以及如何在您的程式設計中使用它們。 文件、 檢視和框架視窗會更詳細地討論[Window 物件](../mfc/window-objects.md)並[文件/檢視架構](../mfc/document-view-architecture.md)。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](../mfc/using-the-classes-to-write-applications-for-windows.md)

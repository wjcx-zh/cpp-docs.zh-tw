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
ms.openlocfilehash: 17956c0b175e978c6e4e2fefcdad5f744929d457
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621828"
---
# <a name="documents-views-and-the-framework"></a>文件、檢視和架構

MFC 架構的核心是文件和檢視的概念。 文件是一種在編輯工作階段與使用者進行互動的資料物件。 它是**由 [檔案] 功能表上**的 [**新增**] 或 [**開啟**] 命令所建立，而且通常會儲存在檔案中。 （衍生自類別的標準 MFC 檔與 `CDocument` 活動文檔和 OLE 複合檔案不同）。「視圖」是一種視窗物件，使用者可以透過它與檔互動。

執行中應用程式的主要物件如下：

- 一個或多個文件。

   您的檔類別（衍生自[CDocument](reference/cdocument-class.md)）會指定您的應用程式資料。

   如果您想要在應用程式中有 OLE 功能，請根據所需的功能類型，從[COleDocument](reference/coledocument-class.md)或其中一個衍生類別衍生您的檔類別。

- 一個或多個檢視。

   您的 view 類別（衍生自[CView](reference/cview-class.md)）是使用者在資料上的「視窗」。 檢視類別可控制使用者如何查看文件的資料以及與其互動。 在某些情況下，您可能想要讓文件擁有多個資料檢視。

   如果您需要滾動，請從[CScrollView](reference/cscrollview-class.md)衍生。 如果您的視圖具有在對話方塊範本資源中配置的使用者介面，則衍生自[CFormView](reference/cformview-class.md)。 若是簡單的文字資料，請使用或衍生自[CEditView](reference/ceditview-class.md)。 若是以表單為基礎的資料存取應用程式（例如資料輸入程式），則衍生自[CRecordView](reference/crecordview-class.md) （適用于 ODBC）。 也可以使用類別[CTreeView](reference/ctreeview-class.md)、 [CListView](reference/clistview-class.md)和[CRichEditView](reference/cricheditview-class.md)。

- 框架視窗

   檢視會顯示在「文件框架視窗」內部。 在 SDI 應用程式中，文件框架視窗也是應用程式的「主框架視窗」。 在 MDI 應用程式中，文件視窗是會顯示在主框架視窗內的子視窗。 您衍生的主框架視窗類別會指定樣式和包含檢視之框架視窗的其他特性。 如果您需要自訂框架視窗，請從[CFrameWnd](reference/cframewnd-class.md)衍生，以自訂 SDI 應用程式的檔框架視窗。 衍生自[CMDIFrameWnd](reference/cmdiframewnd-class.md) ，以自訂 MDI 應用程式的主框架視窗。 也從[CMDIChildWnd](reference/cmdichildwnd-class.md)衍生類別，以自訂您的應用程式支援的每一種不同的 MDI 檔框架視窗。

- 一個或多個文件範本

   文件範本會協調文件、檢視和框架視窗的建立。 衍生自類別[CDocTemplate](reference/cdoctemplate-class.md)的特定檔範本類別，會建立及管理一種類型的所有開啟檔。 支援多種文件類型的應用程式擁有多個文件範本。 使用適用于 SDI 應用程式的類別[CSingleDocTemplate](reference/csingledoctemplate-class.md) ，或使用 MDI 應用程式的類別[CMultiDocTemplate](reference/cmultidoctemplate-class.md) 。

- 應用程式物件

   您的應用程式類別（衍生自[CWinApp](reference/cwinapp-class.md)）會控制上述所有物件，並指定應用程式行為，例如初始化和清除。 應用程式唯一的應用程式物件會建立及管理應用程式所支援任何資料類型的文件範本。

- 執行緒物件

   如果您的應用程式會建立個別的執行執行緒（例如，在背景中執行計算），您將使用衍生自[CWinThread](reference/cwinthread-class.md)的類別。 [CWinApp](reference/cwinapp-class.md)本身衍生自 `CWinThread` ，並代表應用程式中執行的主要執行緒（或主要進程）。 您也可以在次要執行緒中使用 MFC。

在執行中的應用程式中，這些物件會一起回應使用者動作，並透過命令和其他訊息繫結程序在一起。 單一應用程式物件會管理一個或多個文件範本。 每個文件範本會建立和管理一個或多個文件 (根據應用程式為 SDI 還是 MDI 而定)。 使用者透過框架視窗中的檢視來檢視和操作文件。 下圖顯示 SDI 應用程式中這些物件之間的關聯性。

![執行中 SDI 應用程式中的物件](../mfc/media/vc386v1.gif "執行中 SDI 應用程式內的物件") <br/>
執行中 SDI 應用程式內的物件

這一系列的其他文章說明架構工具、MFC 應用程式精靈和資源編輯器如何建立這些物件、它們如何一起運作，以及如何在您的程式設計中使用它們。 [視窗物件](window-objects.md)和[檔/視圖架構](document-view-architecture.md)中會更詳細地討論檔、視圖和框架視窗。

## <a name="see-also"></a>另請參閱

[使用類別來編寫 Windows 應用程式](using-the-classes-to-write-applications-for-windows.md)

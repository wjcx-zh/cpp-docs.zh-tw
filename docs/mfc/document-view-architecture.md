---
title: 文件檢視架構
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: d1b1f80f44fdc66a3174ea75c15e139f98a4520b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775539"
---
# <a name="documentview-architecture"></a>文件/檢視架構

根據預設，MFC 應用程式精靈會建立應用程式基本架構與文件類別和檢視類別。 MFC 會分隔到這兩個類別的資料管理。 文件會將資料儲存和管理列印的資料，並協調更新資料的多個檢視。 此檢視會顯示資料，並管理使用者與其互動，包括選取和編輯。

在此模型中，MFC 文件物件讀取，並將資料寫入至永續性儲存體。 文件可能也會提供介面給資料，無論 （例如資料庫）。 不同的檢視物件會管理資料顯示中，從轉譯至使用者的選取範圍 視窗中的資料和編輯資料。 此檢視會從文件取得顯示的資料，並回到文件的任何資料變更的通訊。

雖然您可以輕鬆地覆寫，或略過的文件/檢視區隔，有令人信服的原因，請依照此模型，在大部分情況下。 最佳的其中一個時，您需要相同的文件，例如試算表和圖表檢視的多個檢視。 文件/檢視模型可讓不同的檢視物件，代表的資料，而程式碼一般給所有的檢視 （例如計算引擎） 可位於文件中的每個檢視。 文件也會在資料有所變更時，更新所有檢視的工作。

MFC 文件/檢視架構讓您更容易支援多個檢視、 多個文件類型、 分隔視窗和其他重要的使用者介面功能。

MFC 架構給使用者和程式設計人員，最明顯的部分是文件和檢視。 大部分的開發架構的應用程式工作會進入撰寫您的文件和檢視類別。 本文章系列說明：

- 文件和檢視與它們互動 framework 中的方式達到目的。

- 您必須如何實作它們。

文件/檢視的核心是四個主要類別：

[CDocument](../mfc/reference/cdocument-class.md) (或[COleDocument](../mfc/reference/coledocument-class.md)) 類別支援用來儲存或控制您的程式資料的物件，並為程式設計人員定義的文件類別中提供的基本功能。 文件表示的使用者通常會隨即開啟，並在 檔案 功能表上的 開啟 命令，並使用 儲存 命令儲存檔案 功能表上的資料單位。

[CView](../mfc/reference/cview-class.md) （或其許多的衍生類別） 提供程式設計人員定義的檢視類別的基本功能。 檢視附加至文件，並做為文件與使用者之間的媒介： 檢視呈現在螢幕上的文件的映像，並將使用者輸入解譯為文件作業。 檢視也會呈現列印和列印預覽影像。

[CFrameWnd](../mfc/reference/cframewnd-class.md) （或一個與其變數） 支援提供的文件的一個或多個檢視周圍框架的物件。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md) (或[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)或是[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) 支援協調的指定類型的一或多個現有文件，以及管理建立正確的物件文件、 檢視和框架視窗物件，該類型。

下圖顯示文件及其檢視之間的關聯性。

![檢視是顯示文件的一部份](../mfc/media/vc379n1.gif "檢視是顯示文件的一部分") <br/>
文件和檢視

類別庫中的文件/檢視實作區隔資料本身從它的顯示畫面和使用者作業的資料。 透過文件類別管理資料的所有變更。 檢視會呼叫這個介面來存取及更新資料。

文件範本建立文件、 其相關聯的檢視和框架檢視框架視窗。 文件範本負責建立和管理一份文件類型的所有文件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [文件/檢視架構的簡介](../mfc/a-portrait-of-the-document-view-architecture.md)

- [文件/檢視架構的優點](../mfc/advantages-of-the-document-view-architecture.md)

- [應用程式精靈所建立的文件和檢視類別](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [文件/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)

- [將多個檢視新增至單一文件](../mfc/adding-multiple-views-to-a-single-document.md)

- [使用文件](../mfc/using-documents.md)

- [使用檢視](../mfc/using-views.md)

- [多重文件類型、檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)

- [初始化及清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [初始化您加入至文件 （& v） 類別](../mfc/creating-new-documents-windows-and-views.md)

- [使用具有文件和檢視資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)

- [使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)

- [範例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面項目](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[框架視窗](../mfc/frame-windows.md)<br/>
[文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[文件/檢視建立](../mfc/document-view-creation.md)<br/>
[建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)

---
title: 文件-檢視架構
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
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624779"
---
# <a name="documentview-architecture"></a>文件/檢視架構

根據預設，MFC 應用程式精靈會建立具有檔類別和 view 類別的應用程式基本架構。 MFC 會將資料管理分成兩個類別。 檔會儲存資料，並管理資料的列印和協調更新多個資料檢視。 此視圖會顯示資料並管理使用者與它的互動，包括選取和編輯。

在此模型中，MFC 檔物件會讀取資料並寫入至持續性儲存體。 檔也可以提供介面給其所在位置的資料（例如在資料庫中）。 另一個 view 物件會管理資料顯示，從將視窗中的資料轉譯為使用者選取和編輯資料。 此視圖會從檔取得顯示資料，並將任何資料變更傳回到檔。

雖然您可以輕鬆地覆寫或忽略檔/視圖區隔，但在大多數情況下，這種模型有一些合理的理由要遵循。 其中一個最棒的是，您需要相同檔的多個視圖，例如試算表和圖表視圖。 檔/視圖模型可讓不同的 view 物件代表資料的每一個觀點，而所有視圖（例如計算引擎）通用的程式碼都可以位於檔中。 當資料變更時，檔也會進行更新所有視圖的工作。

MFC 檔/視圖架構可讓您輕鬆地支援多個視圖、多個檔案類型、分隔視窗，以及其他重要的使用者介面功能。

MFC 架構的各個部分對使用者而言最為可見，而對程式設計人員而言，則是檔和觀點。 您在使用架構開發應用程式時，大部分的工作都是撰寫您的檔和視圖類別。 本文系列將說明：

- 檔和視圖的用途，以及它們在架構中的互動方式。

- 您必須執行的動作。

檔/視圖的核心是四個主要類別：

[CDocument](reference/cdocument-class.md) （或[COleDocument](reference/coledocument-class.md)）類別支援用來儲存或控制程式資料的物件，並提供程式設計人員定義的檔類別的基本功能。 檔代表使用者通常會使用 [檔案] 功能表上的 [開啟] 命令開啟的資料單位，並使用 [檔案] 功能表上的 [儲存] 命令來儲存。

[CView](reference/cview-class.md) （或它的許多衍生類別之一）提供程式設計人員定義之 view 類別的基本功能。 視圖會附加至檔，並做為檔和使用者之間的媒介：此視圖會在畫面上轉譯檔的影像，並將使用者輸入轉譯為檔上的作業。 此視圖也會呈現列印和預覽列印的影像。

[CFrameWnd](reference/cframewnd-class.md) （或它的其中一個變化）支援在檔的一或多個視圖周圍提供框架的物件。

[CDocTemplate](reference/cdoctemplate-class.md) （或[CSingleDocTemplate](reference/csingledoctemplate-class.md)或[CMultiDocTemplate](reference/cmultidoctemplate-class.md)）支援一個物件，它會協調給定類型的一或多個現有檔，並管理為該類型建立正確的檔、視圖和框架視窗物件。

下圖顯示檔與其視圖之間的關聯性。

![檢視是所顯示文件的一部分](../mfc/media/vc379n1.gif "檢視是所顯示文件的一部分") <br/>
檔和視圖

類別庫中的檔/視圖執行會將資料本身與資料的顯示和使用者作業分開。 對資料所做的所有變更都是透過檔類別來管理。 此視圖會呼叫這個介面來存取和更新資料。

檔、其相關聯的視圖，以及框架視窗是由檔範本所建立。 檔範本會負責建立和管理一種檔案類型的所有檔。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [檔/視圖架構的直向](a-portrait-of-the-document-view-architecture.md)

- [檔/視圖架構的優點](advantages-of-the-document-view-architecture.md)

- [應用程式精靈所建立的檔和視圖類別](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [檔/視圖架構的替代方案](alternatives-to-the-document-view-architecture.md)

- [將多個檢視加入至單一文件](adding-multiple-views-to-a-single-document.md)

- [使用文件](using-documents.md)

- [使用檢視](using-views.md)

- [多重文件類型、檢視和框架視窗](multiple-document-types-views-and-frame-windows.md)

- [初始化和清除檔和視圖](initializing-and-cleaning-up-documents-and-views.md)

- [將您自己的新增專案初始化為檔 & 視圖類別](creating-new-documents-windows-and-views.md)

- [使用具有文件和檢視的資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)

- [使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)

- [範例](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>另請參閱

[使用者介面元素](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[框架視窗](frame-windows.md)<br/>
[檔範本和檔/視圖建立程式](document-templates-and-the-document-view-creation-process.md)<br/>
[文件/檢視建立](document-view-creation.md)<br/>
[建立新文件、視窗和檢視](creating-new-documents-windows-and-views.md)

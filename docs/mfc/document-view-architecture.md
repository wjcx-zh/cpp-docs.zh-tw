---
title: 文件檢視架構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9554af9443bbd6a6394789343294630104c96f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="documentview-architecture"></a>文件/檢視架構
依預設，MFC 應用程式精靈建立的應用程式的基本架構文件類別和檢視類別。 MFC 將資料管理分成這兩個類別。 文件會將資料儲存和管理列印資料，並協調更新多個檢視的資料。 檢視會顯示資料，並管理它，包括選取和編輯使用者互動。  
  
 在此模型中，MFC 文件物件讀取，並將資料寫入至永續性儲存體。 文件也會提供介面給資料 （例如資料庫） 所在位置。 不同的檢視物件會從呈現使用者選取的視窗中的資料並編輯資料的管理資料顯示。 此檢視會取得文件中顯示的資料，且會回到文件的任何資料變更。  
  
 雖然您可以輕鬆地覆寫，或略過的文件/檢視區隔，有重要的理由，請依照此模型在大部分情況下。 最佳的其中一個時，您需要多個相同的文件，例如試算表和圖表檢視的檢視。 文件/檢視模型可讓不同的檢視物件代表的資料，而程式碼常見所有檢視 （例如計算引擎） 可都位於文件中的每個檢視。 每當資料變更來更新所有檢視的工作也會在文件。  
  
 MFC 文件/檢視架構可讓您輕鬆支援多個檢視表、 多重文件類型、 分隔視窗和其他重要的使用者介面功能中。  
  
 MFC 架構給使用者和程式設計人員，最明顯的部分是文件和檢視。 大部分的開發架構的應用程式工作便會進入撰寫您的文件和檢視類別。 本文章系列說明：  
  
-   文件和檢視與他們互動 framework 中的方式達到目的。  
  
-   所需的動作來實作它們。  
  
 文件/檢視表的核心是四個主要類別：  
  
 [CDocument](../mfc/reference/cdocument-class.md) (或[COleDocument](../mfc/reference/coledocument-class.md)) 類別支援用來控制您的程式資料，或儲存的物件，並提供的基本功能的程式設計人員定義的文件類別。 文件表示的使用者通常會開啟 檔案 功能表上的 開啟 命令，並 儲存 命令以儲存檔案 功能表上的資料單位。  
  
 [CView](../mfc/reference/cview-class.md) （或其中一個多衍生類別） 的程式設計人員定義的檢視類別中提供的基本功能。 檢視附加至文件，並且會做為文件與使用者之間的媒介： 的檢視會呈現在螢幕上的文件的映像和使用者輸入中解譯作業。 檢視也會呈現列印與列印預覽影像。  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) （或其變化） 支援提供的文件的一個或多個檢視周圍框架的物件。  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) (或[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)或[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) 支援協調的指定類型的一或多個現有文件和管理建立正確的物件文件、 檢視和框架視窗物件，該類型。  
  
 下圖顯示文件和其檢視之間的關聯性。  
  
 ![檢視是顯示文件的部分](../mfc/media/vc379n1.gif "vc379n1")  
文件和檢視  
  
 文件/檢視表中的實作類別庫的資料加以區分本身從它的顯示畫面和使用者的作業資料。 所有資料變更被透過文件類別。 檢視會呼叫這個介面來存取及更新資料。  
  
 文件範本會建立文件、 其相關的檢視和框架檢視之框架視窗。 文件範本負責建立和管理一份文件類型的所有文件。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [文件/檢視架構的簡介](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [文件/檢視架構的優點](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [應用程式精靈所建立的文件和檢視類別](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [文件/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [將多個檢視新增至單一文件](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [使用文件](../mfc/using-documents.md)  
  
-   [使用檢視](../mfc/using-views.md)  
  
-   [多重文件類型、檢視和框架視窗](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [初始化和清除文件和檢視](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [初始化您自己新增至文件和檢視類別](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [使用具有文件和檢視資料庫類別](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [使用不具文件和檢視的資料庫類別](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [範例](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [框架視窗](../mfc/frame-windows.md)   
 [文件範本和文件/檢視建立程序](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [文件/檢視建立](../mfc/document-view-creation.md)   
 [建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)


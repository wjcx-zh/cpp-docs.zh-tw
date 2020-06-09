---
title: 文件範本和文件-檢視建立流程
ms.date: 11/19/2018
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
ms.openlocfilehash: b96a11926927e89890ca268dcff7d347079b25fb
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615781"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>文件範本和文件/檢視建立流程

為了管理使用其相關聯的視圖和框架視窗建立檔的複雜程式，此架構會使用兩個檔範本類別：適用于 SDI 應用程式的[CSingleDocTemplate](reference/csingledoctemplate-class.md)和適用于 MDI 應用程式的[CMultiDocTemplate](reference/cmultidoctemplate-class.md) 。 `CSingleDocTemplate` 一次可以建立和儲存一種類型的文件。 `CMultiDocTemplate` 可保留一種類型的多個開啟文件清單。

某些應用程式支援多種文件類型。 例如，某些應用程式可能支援文字文件和圖形文件。 在這種應用程式中，當使用者選擇 [檔案] 功能表上的 [新增] 命令時會顯示一個對話方塊，其中會顯示可供開啟的新文件類型清單。 對於每種支援的文件類型，應用程式會使用不同的文件範本物件。 下圖說明支援兩種文件類型以及顯示多種開啟文件的 MDI 應用程式組態。

![具有兩個文件類型的 MDI 應用程式](../mfc/media/vc387h1.gif "具有兩個文件類型的 MDI 應用程式") <br/>
具有兩種文件類型的 MDI 應用程式

文件範本是由應用程式物件所建立和維護。 應用程式的 `InitInstance` 函式執行期間要執行的其中一個主要工作即是建構一種或多種適當類型的文件範本。 這項功能會在[建立檔範本](document-template-creation.md)中加以說明。 應用程式物件會將每個文件範本的指標儲存在它的範本清單中，並提供新增文件範本的介面。

如果您需要支援兩種以上的檔案類型，您必須為每種檔案類型新增額外的[AddDocTemplate](reference/cwinapp-class.md#adddoctemplate)呼叫。

其中會根據其在文件範本應用程式清單中的位置，為每種文件範本註冊一個圖示。 文件範本的順序是依照呼叫 `AddDocTemplate` 來新增該文件範本的順序來決定。 MFC 假設應用程式中的第一個「圖示」資源即是應用程式圖示，下一個「圖示」資源則是第一個文件圖示，依此類推。

例如，文件範本使用的是應用程式三個圖示中的第三個圖示。 如果應用程式中存在位於索引 3 的「圖示」資源，則文件範本會使用該圖示。 否則，會使用索引 0 的圖示做為預設值。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](general-mfc-topics.md)<br/>
[文件樣板建立](document-template-creation.md)<br/>
[文件/檢視建立](document-view-creation.md)<br/>
[MFC 物件關聯性](relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](creating-new-documents-windows-and-views.md)

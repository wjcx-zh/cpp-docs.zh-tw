---
title: 文件範本和文件-檢視建立程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 182cf58b3ee712ef0d45719591e967c0b81909bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426519"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>文件範本和文件/檢視建立流程

若要管理複雜的程序建立文件及其相關聯的檢視和框架視窗，架構會使用兩個文件範本類別： [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI 應用程式和[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) MDI 應用程式。 `CSingleDocTemplate` 一次可以建立和儲存一種類型的文件。 `CMultiDocTemplate` 可保留一種類型的多個開啟文件清單。

某些應用程式支援多種文件類型。 例如，某些應用程式可能支援文字文件和圖形文件。 在這種應用程式中，當使用者選擇 [檔案] 功能表上的 [新增] 命令時會顯示一個對話方塊，其中會顯示可供開啟的新文件類型清單。 對於每種支援的文件類型，應用程式會使用不同的文件範本物件。 下圖說明支援兩種文件類型以及顯示多種開啟文件的 MDI 應用程式組態。

![有兩種文件類型的 MDI 應用程式](../mfc/media/vc387h1.gif "vc387h1")兩個文件類型的 MDI 應用程式

文件範本是由應用程式物件所建立和維護。 應用程式的 `InitInstance` 函式執行期間要執行的其中一個主要工作即是建構一種或多種適當類型的文件範本。 這項功能所述[文件樣板建立](../mfc/document-template-creation.md)。 應用程式物件會將每個文件範本的指標儲存在它的範本清單中，並提供新增文件範本的介面。

如果您需要支援兩個或多個文件類型，您必須將額外的呼叫加入[Initinstance](../mfc/reference/cwinapp-class.md#adddoctemplate)針對每個文件類型。

其中會根據其在文件範本應用程式清單中的位置，為每種文件範本註冊一個圖示。 文件範本的順序是依照呼叫 `AddDocTemplate` 來新增該文件範本的順序來決定。 MFC 假設應用程式中的第一個「圖示」資源即是應用程式圖示，下一個「圖示」資源則是第一個文件圖示，依此類推。

例如，文件範本使用的是應用程式三個圖示中的第三個圖示。 如果應用程式中存在位於索引 3 的「圖示」資源，則文件範本會使用該圖示。 否則，會使用索引 0 的圖示做為預設值。

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)<br/>
[文件樣板建立](../mfc/document-template-creation.md)<br/>
[文件/檢視建立](../mfc/document-view-creation.md)<br/>
[MFC 物件關聯性](../mfc/relationships-among-mfc-objects.md)<br/>
[建立新文件、視窗和檢視](../mfc/creating-new-documents-windows-and-views.md)


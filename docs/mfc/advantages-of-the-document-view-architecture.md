---
title: 文件檢視架構的優點
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: e250630bf3c9714fc01ff66b66fba3ac0d5b1cc1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265453"
---
# <a name="advantages-of-the-documentview-architecture"></a>文件/檢視架構的優點

若要使用 MFC 文件/檢視架構的主要優點是架構特別支援相同的文件的多個檢視。 （如果您不需要多個檢視的文件/檢視表的小型負擔增加會過多的應用程式中，您可以避免架構。 [文件/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)。)

假設您的應用程式可讓使用者在試算表或圖表格式檢視數值資料。 使用者可能會想要查看同時這兩個未經處理資料，請在試算表和圖表所產生的資料。 在不同的框架視窗中或在單一視窗內的分割窗格中，您就會顯示這些不同的檢視。 現在假設使用者可以編輯試算表，請參閱中的資料所做的變更立即反映在圖表中。

在 MFC 中，試算表檢視和 [圖表] 檢視會根據衍生自 CView 的不同類別。 這兩個檢視是單一文件物件相關聯。 文件會儲存資料 （或可能會在從資料庫取得）。 這兩個檢視存取文件，並顯示它們從其擷取的資料。

當使用者更新其中一個檢視，檢視物件呼叫`CDocument::UpdateAllViews`。 該函式會通知所有的文件的檢視，以及每個檢視使用文件的最新資料自行更新。 單一呼叫`UpdateAllViews`同步處理不同的檢視。

這種情況下會很難不使用的資料隔離的程式碼從檢視中，特別是當檢視儲存資料本身。 文件/檢視，您可輕鬆。 此架構會為您的大部分的協調工作。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [文件/檢視的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)

- [CDocument](../mfc/reference/cdocument-class.md)

- [CView](../mfc/reference/cview-class.md)

- [CDocument::UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)

- [CView::GetDocument](../mfc/reference/cview-class.md#getdocument)

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)

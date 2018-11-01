---
title: 文件檢視架構的簡介
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: a4d89189b5389685be6b69c8502ffedb8aa731e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567098"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>文件/檢視架構的簡介

在一般 MFC 應用程式中文件和檢視是成對的。 資料會儲存在文件中，不過檢視具有資料的存取權限。 將文件從檢視中分離，會將資料的儲存和維護從其顯示分隔開來。

## <a name="gaining-access-to-document-data-from-the-view"></a>從檢視獲得文件資料的存取權

檢視存取其文件的資料不論是透過[GetDocument](../mfc/reference/cview-class.md#getdocument)函式，它會傳回指標至文件，或藉由檢視類別 c + +`friend`文件類別。 當檢視準備繪製或進行操作時，會利用其資料存取權來取得資料。

例如，從檢視[OnDraw](../mfc/reference/cview-class.md#ondraw)成員函式，檢視使用`GetDocument`來取得文件指標。 然後，它會使用該指標來存取文件中的 `CString` 資料成員。 檢視會傳遞字串至 `TextOut` 函式。 若要查看此範例的程式碼，請參閱[檢視中繪製](../mfc/drawing-in-a-view.md)。

## <a name="user-input-to-the-view"></a>使用者輸入到檢視

檢視也會其本身內將按一下滑鼠動作解譯為選取或編輯資料。 同樣地，也可以將按鍵輸入解譯為資料輸入或編輯。 假設使用者在管理文字的檢視中輸入字串。 檢視會取得文件的指標，並使用指標將新資料傳遞至文件 (以某些資料結構儲存資料)。

## <a name="updating-multiple-views-of-the-same-document"></a>更新相同文件的多個檢視

相同的文件的多個檢視的應用程式中 — 例如文字編輯器中的分隔視窗，檢視第一次將新的資料傳遞至文件。 然後它會呼叫文件[UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews)成員函式，它會告訴所有檢視自行更新，以反映新的資料的文件。 這會同步處理檢閱。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [文件/檢視架構的優點](../mfc/advantages-of-the-document-view-architecture.md)

- [文件/檢視架構的替代方案](../mfc/alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>另請參閱

[文件/檢視架構](../mfc/document-view-architecture.md)


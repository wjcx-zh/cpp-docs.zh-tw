---
title: 文件-檢視架構的簡介
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
ms.openlocfilehash: f0e71c42004b5409eeb6f5e2ddabd33296cf5f49
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623440"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>文件/檢視架構的簡介

在一般 MFC 應用程式中文件和檢視是成對的。 資料會儲存在文件中，不過檢視具有資料的存取權限。 將文件從檢視中分離，會將資料的儲存和維護從其顯示分隔開來。

## <a name="gaining-access-to-document-data-from-the-view"></a>從檢視獲得文件資料的存取權

此視圖會使用[GetDocument](reference/cview-class.md#getdocument)函式存取其檔的資料，此函式會傳回檔的指標，或將 view 類別設為檔類別的 c + + `friend` 。 當檢視準備繪製或進行操作時，會利用其資料存取權來取得資料。

例如，從 view 的[OnDraw](reference/cview-class.md#ondraw)成員函式中，view 會使用 `GetDocument` 來取得檔指標。 然後，它會使用該指標來存取文件中的 `CString` 資料成員。 檢視會傳遞字串至 `TextOut` 函式。 若要查看此範例的程式碼，請參閱[在視圖中繪製](drawing-in-a-view.md)。

## <a name="user-input-to-the-view"></a>使用者輸入到檢視

檢視也會其本身內將按一下滑鼠動作解譯為選取或編輯資料。 同樣地，也可以將按鍵輸入解譯為資料輸入或編輯。 假設使用者在管理文字的檢視中輸入字串。 檢視會取得文件的指標，並使用指標將新資料傳遞至文件 (以某些資料結構儲存資料)。

## <a name="updating-multiple-views-of-the-same-document"></a>更新相同文件的多個檢視

在應用程式中有同一份文件的多個檢視 (例如，文字編輯器中的分隔視窗)，檢視首先會將新資料傳遞至文件。 然後，它會呼叫檔的[UpdateAllViews](reference/cdocument-class.md#updateallviews)成員函式，告訴檔的所有視圖都要自行更新，以反映新的資料。 這會同步處理檢閱。

### <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [檔/視圖架構的優點](advantages-of-the-document-view-architecture.md)

- [檔/視圖架構的替代方案](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>另請參閱

[檔/視圖架構](document-view-architecture.md)

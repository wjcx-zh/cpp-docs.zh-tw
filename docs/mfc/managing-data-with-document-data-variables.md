---
title: 使用文件資料變數管理資料
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151991"
---
# <a name="managing-data-with-document-data-variables"></a>使用文件資料變數管理資料

實作您的文件資料做為您的文件類別的成員變數。 比方說，Scribble 程式宣告型別的資料成員`CObList`— 將指標儲存至的連結的清單`CObject`物件。 這份清單用來儲存構成手繪線條的點的陣列。

實作您的文件的成員資料的方式，取決於您的應用程式的本質。 為了協助您放大，MFC 提供的 「 集合類別 」 的群組-陣列、 清單和對應 （字典），包括基礎集合C++範本 — 以及類別來封裝各種常見資料類型，例如`CString`， `CRect`，`CPoint`， `CSize`，和`CTime`。 如需有關這些類別的詳細資訊，請參閱 <<c0> [ 類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考 》*。

當您定義您的文件的成員資料時，通常會將成員函式加入至設定並取得資料的項目以及執行其他實用的作業，在其上的文件類別中。

您的檢視會使用的文件中，然後再安裝在建立時檢視中檢視的指標，以存取文件物件。 您可以藉由呼叫擷取檢視的成員函式中的 this 指標`CView`成員函式`GetDocument`。 請務必在這個指標轉換成您自己的文件類型。 然後，您可以透過指標存取公用文件成員。

如果頻繁的資料傳輸需要直接存取，或您想要使用的文件類別的非公用成員，您可能想要讓您的檢視類別的 friend (在C++條款) 的文件類別。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)

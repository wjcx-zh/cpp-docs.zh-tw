---
title: 使用文件資料變數管理資料 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0a1db1e15733a0a3cd217c44aaaa325c146ee64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435879"
---
# <a name="managing-data-with-document-data-variables"></a>使用文件資料變數管理資料

實作您的文件資料做為您的文件類別的成員變數。 比方說，Scribble 程式宣告型別的資料成員`CObList`— 將指標儲存至的連結的清單`CObject`物件。 這份清單用來儲存構成手繪線條的點的陣列。

實作您的文件的成員資料的方式，取決於您的應用程式的本質。 為了協助您放大，MFC 提供的 「 集合類別 」 的群組-陣列、 清單和對應 （字典），包括 c + + 範本為基礎的集合，以及這類封裝各種常見的資料類型的類別`CString`， `CRect`， `CPoint`， `CSize`，和`CTime`。 如需有關這些類別的詳細資訊，請參閱 <<c0> [ 類別庫概觀](../mfc/class-library-overview.md)中*MFC 參考 》*。

當您定義您的文件的成員資料時，通常會將成員函式加入至設定並取得資料的項目以及執行其他實用的作業，在其上的文件類別中。

您的檢視會使用的文件中，然後再安裝在建立時檢視中檢視的指標，以存取文件物件。 您可以藉由呼叫擷取檢視的成員函式中的 this 指標`CView`成員函式`GetDocument`。 請務必在這個指標轉換成您自己的文件類型。 然後，您可以透過指標存取公用文件成員。

如果頻繁的資料傳輸需要直接存取，或您想要使用的文件類別的非公用成員，您可能想要讓您的檢視類別的文件類別的 friend （在 c + + 詞彙）。

## <a name="see-also"></a>另請參閱

[使用文件](../mfc/using-documents.md)


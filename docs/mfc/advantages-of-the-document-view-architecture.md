---
title: 文件-檢視架構的優點
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 80f7141ec62d509defdea361586399bd375df0d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623283"
---
# <a name="advantages-of-the-documentview-architecture"></a>文件/檢視架構的優點

使用 MFC 檔/視圖架構的主要優點是，架構支援相同檔的多個觀點，特別是如此。 （如果您不需要多個視圖，而且檔/視圖的小型額外負荷在應用程式中過多，您可以避免架構。 [檔/視圖架構的替代](alternatives-to-the-document-view-architecture.md)專案）。

假設您的應用程式可讓使用者以試算表形式或圖表形式來查看數值資料。 使用者可能會想要同時查看原始資料、試算表表單，以及資料所產生的圖表。 您會在個別的框架視窗中，或在單一視窗內的分隔器窗格中顯示這些個別的視圖。 現在，假設使用者可以編輯試算表中的資料，並看到變更立即反映在圖表中。

在 MFC 中，試算表視圖和圖表視圖會以衍生自 CView 的不同類別為基礎。 這兩個視圖都會與單一檔物件相關聯。 檔會儲存資料（或可能從資料庫取得）。 這兩個視圖都會存取檔，並顯示從中抓取的資料。

當使用者更新其中一個視圖時，該 view 物件會呼叫 `CDocument::UpdateAllViews` 。 該函式會通知所有檔的視圖，而每個視圖都會使用檔中的最新資料來更新本身。 用來同步處理 `UpdateAllViews` 不同視圖的單一呼叫。

這種情況很難撰寫程式碼，而不需要將資料與 view 分開，特別是當 views 儲存資料本身時。 使用檔/視圖，很容易。 架構會為您執行大部分的協調工作。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [檔/視圖的替代專案](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument：： UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView：： GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>另請參閱

[檔/視圖架構](document-view-architecture.md)

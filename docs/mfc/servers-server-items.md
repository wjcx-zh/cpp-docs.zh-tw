---
title: 伺服器：伺服器項目
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: abee619aa921b3e036a2bbeb1b4f5ae08d83f5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307844"
---
# <a name="servers-server-items"></a>伺服器：伺服器項目

當容器啟動伺服器以便使用者可以編輯內嵌或連結的 OLE 項目時，伺服器應用程式會建立「伺服器項目」。 伺服器項目是其類別衍生自 `COleServerItem` 的物件，在伺服器文件和容器應用程式之間提供介面。

`COleServerItem` 類別通常會定義由 OLE 呼叫的數個可覆寫成員函式，以回應容器的要求。 伺服器項目可代表伺服器文件的一部分或整個文件。 當 OLE 項目內嵌於容器文件中時，伺服器項目代表整個伺服器文件。 當 OLE 項目為連結時，伺服器項目可能表示伺服器文件或整份文件的一部分，視連結是連至一部分或整體。

在  [HIERSVR](../overview/visual-cpp-samples.md)範例，例如，伺服器項目類別`CServerItem`，有一個為類別的物件指標的成員`CServerNode`。 `CServerNode`物件是 HIERSVR 應用程式的文件，也就是樹狀結構中的節點。 當`CServerNode`物件是根節點，`CServerItem`物件代表整份文件。 當`CServerNode`物件是一個子節點，`CServerItem`物件都代表在文件的一部分。 請參閱 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)如需這種互動的範例。

##  <a name="_core_implementing_server_items"></a> 實作伺服器項目

如果您使用應用程式精靈產生應用程式的起始程式碼，則要在起始程式碼中包含伺服器項目的話，您只要從 [OLE 選項] 頁面選擇其中一個伺服器選項即可。 如果您將伺服器項目加入至現有的應用程式，請執行下列步驟：

#### <a name="to-implement-a-server-item"></a>實作伺服器項目

1. 從 `COleServerItem` 衍生類別。

1. 在衍生類別中，覆寫 `OnDraw` 成員函式。

   這個架構會呼叫 `OnDraw` 以轉譯 OLE 項目為中繼檔。 容器應用程式會使用此中繼檔轉譯項目。 您的應用程式的檢視類別也有一個 `OnDraw` 成員函式，用來在伺服器應用程式作用中時轉譯項目。

1. 為您的伺服器文件類別實作 `OnGetEmbeddedItem` 的覆寫。 如需詳細資訊，請參閱文章[伺服器：實作伺服器文件](../mfc/servers-implementing-server-documents.md)和 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)。

1. 實作您的伺服器項目類別的 `OnGetExtent` 成員函式。 架構會呼叫這個函式以擷取項目的大小。 預設實作不做任何動作。

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> 伺服器項目架構的秘訣

如中所述[實作伺服器項目](#_core_implementing_server_items)，伺服器應用程式必須能夠在伺服器檢視和容器應用程式所使用的中繼檔中的項目呈現。 在 Microsoft Foundation 類別庫的應用程式架構中，檢視類別的`OnDraw`正在進行編輯時，成員函式會轉譯項目 (請參閱 < [cview:: Ondraw](../mfc/reference/cview-class.md#ondraw)在*類別庫參考*). 伺服器項目的`OnDraw`在所有其他情況下在中繼檔轉譯項目 (請參閱 < [coleserveritem:: Ondraw](../mfc/reference/coleserveritem-class.md#ondraw))。

您可以在您的伺服器文件類別中撰寫 Helper 函式並在您的檢視和伺服器項目類別中從 `OnDraw` 函式呼叫它們，以避免程式碼的重複。 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)會使用這項策略： 函式`CServerView::OnDraw`並`CServerItem::OnDraw`這兩者都會呼叫`CServerDoc::DrawTree`轉譯項目。

因為檢視和項目是在不同情況下繪製，所以檢視和項目都具有 `OnDraw` 成員函式。 檢視中必須考慮到像縮放、選項大小和範圍、裁剪和使用者介面項目 (例如捲軸) 之類的因素。 另一方面，伺服器項目一律都會繪製整個 OLE 物件。

如需詳細資訊，請參閱 < [cview:: Ondraw](../mfc/reference/cview-class.md#ondraw)， [COleServerItem](../mfc/reference/coleserveritem-class.md)， [coleserveritem:: Ondraw](../mfc/reference/coleserveritem-class.md#ondraw)，和[Coleserveritem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)中*類別程式庫參考*。

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)

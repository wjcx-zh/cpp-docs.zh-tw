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
ms.openlocfilehash: 8ae24104a30a0b44e92b889006907911124310f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355117"
---
# <a name="servers-server-items"></a>伺服器：伺服器項目

當容器啟動伺服器以便使用者可以編輯內嵌或連結的 OLE 項目時，伺服器應用程式會建立「伺服器項目」。 伺服器項目是其類別衍生自 `COleServerItem` 的物件，在伺服器文件和容器應用程式之間提供介面。

`COleServerItem` 類別通常會定義由 OLE 呼叫的數個可覆寫成員函式，以回應容器的要求。 伺服器項目可代表伺服器文件的一部分或整個文件。 當 OLE 項目內嵌於容器文件中時，伺服器項目代表整個伺服器文件。 當 OLE 項目為連結時，伺服器項目可能表示伺服器文件或整份文件的一部分，視連結是連至一部分或整體。

例如,在[HIERSVR](../overview/visual-cpp-samples.md)示例中,伺服器`CServerItem`項類的成員是`CServerNode`指向類 物件的指標。 該`CServerNode`對像是 HIERSVR 應用程式文件中的節點,該節點是樹。 當`CServerNode`物件是根節點時`CServerItem`, 該物件表示整個文檔。 當`CServerNode`對物件是子節點`CServerItem`時, 該物件表示文檔的一部分。 有關此互動的示例,請參閱 MFC OLE 範例[HIERSVR。](../overview/visual-cpp-samples.md)

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a>實現伺服器項目

如果您使用應用程式精靈產生應用程式的起始程式碼，則要在起始程式碼中包含伺服器項目的話，您只要從 [OLE 選項] 頁面選擇其中一個伺服器選項即可。 如果您將伺服器項目加入至現有的應用程式，請執行下列步驟：

#### <a name="to-implement-a-server-item"></a>實作伺服器項目

1. 從 `COleServerItem` 衍生類別。

1. 在衍生類別中，覆寫 `OnDraw` 成員函式。

   這個架構會呼叫 `OnDraw` 以轉譯 OLE 項目為中繼檔。 容器應用程式會使用此中繼檔轉譯項目。 您的應用程式的檢視類別也有一個 `OnDraw` 成員函式，用來在伺服器應用程式作用中時轉譯項目。

1. 為您的伺服器文件類別實作 `OnGetEmbeddedItem` 的覆寫。 有關詳細資訊,請參閱文章[「伺服器:實現伺服器文檔](../mfc/servers-implementing-server-documents.md)」和 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)。

1. 實作您的伺服器項目類別的 `OnGetExtent` 成員函式。 架構會呼叫這個函式以擷取項目的大小。 預設實作不做任何動作。

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a>伺服器項目架構結構提示

如[實現伺服器項](#_core_implementing_server_items)中所述,伺服器應用程式必須能夠在伺服器的檢視和容器應用程式使用的元檔中呈現項。 在 Microsoft 基礎類庫的應用程式體系結構中,視`OnDraw`圖類的成員函數在編輯專案時呈現該專案(請參閱*類庫參考*中的[CView:OnDraw)。](../mfc/reference/cview-class.md#ondraw) 伺服器項在`OnDraw`所有其他情況下將項呈現為元檔(請參閱[COleServerItem:onDraw](../mfc/reference/coleserveritem-class.md#ondraw))。

您可以在您的伺服器文件類別中撰寫 Helper 函式並在您的檢視和伺服器項目類別中從 `OnDraw` 函式呼叫它們，以避免程式碼的重複。 MFC OLE 範例[HIERSVR](../overview/visual-cpp-samples.md)`CServerView::OnDraw`使用此`CServerItem::OnDraw`策略:`CServerDoc::DrawTree`函數 和兩個調用來呈現專案。

因為檢視和項目是在不同情況下繪製，所以檢視和項目都具有 `OnDraw` 成員函式。 檢視中必須考慮到像縮放、選項大小和範圍、裁剪和使用者介面項目 (例如捲軸) 之類的因素。 另一方面，伺服器項目一律都會繪製整個 OLE 物件。

有關詳細資訊,請參閱[CView:onDraw、COleServer](../mfc/reference/cview-class.md#ondraw)[專案](../mfc/reference/coleserveritem-class.md)[、COleServer 專案::onDraw](../mfc/reference/coleserveritem-class.md#ondraw)和[COleServerDoc:在](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)*類庫引用*中獲取嵌入專案。

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)

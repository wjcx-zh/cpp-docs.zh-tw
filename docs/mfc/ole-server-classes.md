---
title: OLE 伺服器類別
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 92dec514611dcce7d6c666fdd271843e69561637
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447599"
---
# <a name="ole-server-classes"></a>OLE 伺服器類別

這些類別是由伺服器應用程式所使用。 伺服器檔衍生自 `COleServerDoc`，而不是從 `CDocument`。 請注意，因為 `COleServerDoc` 衍生自 `COleLinkingDoc`，伺服器檔也可以是支援連結的容器。

`COleServerItem` 類別代表可以內嵌在另一份檔或連結至之檔的檔或部分。

`COleIPFrameWnd` 和 `COleResizeBar` 支援就地編輯，而物件位於容器中，而 `COleTemplateServer` 支援建立檔/視圖組，因此可以編輯來自其他應用程式的 OLE 物件。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
當做伺服器應用程式檔類別的基類使用。 `COleServerDoc` 物件透過與 `COleServerItem` 物件的互動，提供大量的伺服器支援。 視覺編輯功能是使用類別庫的檔/視圖架構來提供。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
`COleClientItem` 和 `COleServerItem`的抽象基類。 衍生自 `CDocItem` 的類別物件代表檔的部分。

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
用來代表要 `COleServerDoc` 專案的 OLE 介面。 通常會有一個 `COleServerDoc` 物件，代表檔的內嵌部分。 在支援檔部分連結的伺服器中，可以有許多 `COleServerItem` 物件，其中每一個都代表檔部分的連結。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
當伺服器檔正在進行編輯時，提供視圖的框架視窗。

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
提供就地調整大小的標準使用者介面。 這個類別的物件一律會與 `COleIPFrameWnd` 物件搭配使用。

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
用來使用架構的檔/視圖架構來建立檔。 `COleTemplateServer` 物件將大部分的工作委派給關聯的 `CDocTemplate` 物件。

[COleException](../mfc/reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)

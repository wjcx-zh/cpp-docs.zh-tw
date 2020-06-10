---
title: OLE 伺服器類別
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 06f5cf0985756506e42c7ad9fde24641b5a0ce93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619859"
---
# <a name="ole-server-classes"></a>OLE 伺服器類別

這些類別是由伺服器應用程式所使用。 伺服器檔衍生自， `COleServerDoc` 而不是從 `CDocument` 。 請注意，因為 `COleServerDoc` 衍生自 `COleLinkingDoc` ，所以伺服器檔也可以是支援連結的容器。

`COleServerItem`類別代表可以內嵌在另一份檔或連結至之檔的檔或部分。

`COleIPFrameWnd`和 `COleResizeBar` 支援在物件位於容器中時進行就地編輯，並 `COleTemplateServer` 支援建立檔/視圖組，因此可以編輯來自其他應用程式的 OLE 物件。

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
當做伺服器應用程式檔類別的基類使用。 `COleServerDoc`物件透過與物件的互動，提供大量的伺服器支援 `COleServerItem` 。 視覺編輯功能是使用類別庫的檔/視圖架構來提供。

[CDocItem](reference/cdocitem-class.md)<br/>
和的抽象基類 `COleClientItem` `COleServerItem` 。 衍生自的類別物件 `CDocItem` 代表檔的各部分。

[COleServerItem](reference/coleserveritem-class.md)<br/>
用來代表專案的 OLE 介面 `COleServerDoc` 。 通常會有一個 `COleServerDoc` 代表檔內嵌部分的物件。 在支援檔元件之連結的伺服器中，可以有許多 `COleServerItem` 物件，其中每一個都代表檔部分的連結。

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
當伺服器檔正在進行編輯時，提供視圖的框架視窗。

[COleResizeBar](reference/coleresizebar-class.md)<br/>
提供就地調整大小的標準使用者介面。 這個類別的物件一律會與物件搭配使用 `COleIPFrameWnd` 。

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
用來使用架構的檔/視圖架構來建立檔。 物件會將 `COleTemplateServer` 其大部分的工作委派給相關聯的 `CDocTemplate` 物件。

[COleException](reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)

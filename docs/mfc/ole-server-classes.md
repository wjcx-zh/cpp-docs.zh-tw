---
title: OLE 伺服器類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 99dd7f58b862fadc86ee2515bb8ef2008bc538fa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289573"
---
# <a name="ole-server-classes"></a>OLE 伺服器類別

這些類別會使用伺服器應用程式。 伺服器文件衍生自`COleServerDoc`而不是從`CDocument`。 請注意，因為`COleServerDoc`衍生自`COleLinkingDoc`，伺服器文件也可以支援連結的容器。

`COleServerItem`類別代表文件或其他文件中內嵌或連結至文件的一部分。

`COleIPFrameWnd` 並`COleResizeBar`支援就地編輯，而物件是在容器中，和`COleTemplateServer`支援文件/檢視組的建立，因此可以編輯從其他應用程式的 OLE 物件。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
做為伺服器應用程式的文件類別的基底的類別。 `COleServerDoc` 物件提供與互動的伺服器支援大量`COleServerItem`物件。 視覺化的編輯功能被提供使用類別庫的文件/檢視架構。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象的基底類別`COleClientItem`和`COleServerItem`。 類別的物件衍生自`CDocItem`代表文件的部分。

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
用來代表的 OLE 介面`COleServerDoc`項目。 有一個通常`COleServerDoc`物件，表示文件中內嵌的一部份。 在 支援的文件的組件的連結的伺服器，可以有許多`COleServerItem`物件，每一個都代表連結至文件的一部分。

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
當就地編輯伺服器文件時，則您可以提供檢視框架視窗。

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
提供的標準使用者介面就地調整大小。 這個類別的物件一律用於搭配`COleIPFrameWnd`物件。

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
用來建立使用架構的文件/檢視架構的文件。 A`COleTemplateServer`物件會委派至相關聯工作的大部分`CDocTemplate`物件。

[COleException](../mfc/reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

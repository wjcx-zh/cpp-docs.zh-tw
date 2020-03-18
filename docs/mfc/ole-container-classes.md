---
title: OLE 容器類別
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447663"
---
# <a name="ole-container-classes"></a>OLE 容器類別

這些類別是由容器應用程式所使用。 `COleLinkingDoc` 和 `COleDocument` 都會管理 `COleClientItem` 物件的集合。 根據您是否想要支援內嵌在檔中之物件的連結，您可以從 `COleLinkingDoc` 或 `COleDocument`衍生您的檔類別，而不是從 `CDocument`。

使用 `COleClientItem` 物件，表示檔中從另一份檔內嵌，或連結至另一份檔的每個 OLE 專案。

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
支援活動文檔內含專案。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用於複合檔案的執行，以及基本容器支援。 作為衍生自 `CDocItem`之類別的容器。 這個類別可用來做為容器檔案的基類，而且是 `COleServerDoc`的基類。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
衍生自 `COleDocument` 的類別，提供連結的基礎結構。 您應該從這個類別衍生容器應用程式的檔類別，而不是從 `COleDocument`，如果您想要它們支援内嵌物件的連結。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
維護 rich edit 控制項中的 OLE 用戶端專案清單。 與[CRichEditView](../mfc/reference/cricheditview-class.md)和[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)搭配使用。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
`COleClientItem` 和 `COleServerItem`的抽象基類。 衍生自 `CDocItem` 的類別物件代表檔的部分。

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
用戶端專案類別，表示與內嵌或連結的 OLE 專案之連接的用戶端。 從這個類別衍生您的用戶端專案。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
當搭配 `CRichEditView` 和 `CRichEditDoc`使用時，提供 rtf 編輯控制項中所儲存之 OLE 專案的用戶端存取。

[COleException](../mfc/reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別總覽](../mfc/class-library-overview.md)

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
ms.openlocfilehash: 596b94e7fdbb5d9dc1862867001f6c01c1aea7b2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617800"
---
# <a name="ole-container-classes"></a>OLE 容器類別

這些類別是由容器應用程式所使用。 `COleLinkingDoc`和都會 `COleDocument` 管理物件的集合 `COleClientItem` 。 `CDocument` `COleLinkingDoc` `COleDocument` 視您是否想要支援內嵌在檔中的物件連結而定，您可以從或衍生您的檔類別，而不是從派生您的檔類別。

使用 `COleClientItem` 物件來代表檔中從另一份檔內嵌的每個 OLE 專案，或是另一份檔的連結。

[COleDocObjectItem](reference/coledocobjectitem-class.md)<br/>
支援活動文檔內含專案。

[COleDocument](reference/coledocument-class.md)<br/>
用於複合檔案的執行，以及基本容器支援。 作為衍生自之類別的容器 `CDocItem` 。 這個類別可用來做為容器檔案的基類，而且是的基類 `COleServerDoc` 。

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
衍生自的類別 `COleDocument` ，可提供要連結的基礎結構。 您應該從這個類別衍生容器應用程式的檔類別，而不是從 `COleDocument` ，如果您想要它們支援内嵌物件的連結。

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
維護 rich edit 控制項中的 OLE 用戶端專案清單。 與[CRichEditView](reference/cricheditview-class.md)和[CRichEditCntrItem](reference/cricheditcntritem-class.md)搭配使用。

[CDocItem](reference/cdocitem-class.md)<br/>
和的抽象基類 `COleClientItem` `COleServerItem` 。 衍生自的類別物件 `CDocItem` 代表檔的各部分。

[COleClientItem](reference/coleclientitem-class.md)<br/>
用戶端專案類別，表示與內嵌或連結的 OLE 專案之連接的用戶端。 從這個類別衍生您的用戶端專案。

[CRichEditCntrItem](reference/cricheditcntritem-class.md)<br/>
當與和搭配使用時，提供儲存在 rich edit 控制項中之 OLE 專案的用戶端存取 `CRichEditView` `CRichEditDoc` 。

[COleException](reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)

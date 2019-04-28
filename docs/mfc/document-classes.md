---
title: 文件類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219791"
---
# <a name="document-classes"></a>文件類別

文件範本物件所建立的文件類別物件會管理應用程式的資料。 您將您的文件衍生類別，來自其中一個類別。

文件類別物件互動檢視物件。 檢視物件表示視窗的工作區、 顯示文件的資料，並允許使用者與它互動。 文件和檢視會建立文件範本物件。

[CDocument](../mfc/reference/cdocument-class.md)<br/>
應用程式特定的文件基底類別。 衍生您的文件類別或類別從`CDocument`。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用於複合文件的實作，以及基本的容器支援。 做為容器的類別衍生自[CDocItem](../mfc/reference/cdocitem-class.md)。 這個類別可用來當做基底類別容器文件，而且是基底類別`COleServerDoc`。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
類別衍生自`COleDocument`所提供的基礎結構進行連結。 您應該將文件類別衍生自這個類別而不是從應用程式容器`COleDocument`如果您想要它們支援內嵌物件連結。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
會維護 rich edit 控制項中的 OLE 用戶端項目清單。 搭配[CRichEditView](../mfc/reference/cricheditview-class.md)並[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
做為伺服器應用程式的文件類別的基底的類別。 `COleServerDoc` 物件提供與互動的伺服器支援大量[COleServerItem](../mfc/reference/coleserveritem-class.md)物件。 視覺化的編輯功能被提供使用類別庫的文件/檢視架構。

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
提供，與[CHtmlEditView](../mfc/reference/chtmleditview-class.md)，在 MFC 的文件檢視架構內容中的 HTML WebBrowser 編輯平台的功能。

## <a name="related-classes"></a>相關的類別

文件類別物件可以是持續性 — 換句話說，它們可以在儲存媒體中撰寫它們的狀態和讀回。 MFC 提供`CArchive`類別來簡化將文件的資料傳輸至儲存媒體。

[CArchive](../mfc/reference/carchive-class.md)<br/>
會與合作[CFile](../mfc/reference/cfile-class.md)物件來實作透過序列化物件的永續性儲存體 (請參閱[cobject:: Serialize](../mfc/reference/cobject-class.md#serialize))。

文件也可以包含 OLE 物件。 `CDocItem` 是伺服器和用戶端項目的基底類別。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象的基底類別[COleClientItem](../mfc/reference/coleclientitem-class.md)並[COleServerItem](../mfc/reference/coleserveritem-class.md)。 類別的物件衍生自`CDocItem`代表文件的部分。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

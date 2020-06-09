---
title: 文件類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615796"
---
# <a name="document-classes"></a>文件類別

檔類別物件是由檔範本物件所建立，用來管理應用程式的資料。 您將從這些類別的其中一個衍生您的檔類別。

檔類別物件與 view 物件互動。 View 物件代表視窗的工作區、顯示檔的資料，並允許使用者與之互動。 檔和瀏覽器是由檔範本物件所建立。

[CDocument](reference/cdocument-class.md)<br/>
應用程式特定檔的基類。 從衍生您的檔類別或類別 `CDocument` 。

[COleDocument](reference/coledocument-class.md)<br/>
用於複合檔案的執行，以及基本容器支援。 作為衍生自[CDocItem](reference/cdocitem-class.md)之類別的容器。 這個類別可用來做為容器檔案的基類，而且是的基類 `COleServerDoc` 。

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
衍生自的類別 `COleDocument` ，可提供要連結的基礎結構。 您應該從這個類別衍生容器應用程式的檔類別，而不是從 `COleDocument` ，如果您想要它們支援内嵌物件的連結。

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
維護 rich edit 控制項中的 OLE 用戶端專案清單。 與[CRichEditView](reference/cricheditview-class.md)和[CRichEditCntrItem](reference/cricheditcntritem-class.md)搭配使用。

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
當做伺服器應用程式檔類別的基類使用。 `COleServerDoc`物件透過與[COleServerItem](reference/coleserveritem-class.md)物件的互動，提供大量的伺服器支援。 視覺編輯功能是使用類別庫的檔/視圖架構來提供。

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
透過[CHtmlEditView](reference/chtmleditview-class.md)，在 MFC 檔視圖架構的內容中提供 WebBrowser HTML 編輯平臺的功能。

## <a name="related-classes"></a>相關類別

檔類別物件可以是持續性的，也就是說，它們可以將其狀態寫入儲存媒體，並將其讀回。 MFC 提供的 `CArchive` 類別可加速將檔的資料傳送至儲存媒體。

[CArchive](reference/carchive-class.md)<br/>
具有[CFile](reference/cfile-class.md)物件的會合作，可透過序列化來執行物件的持續性儲存（請參閱[CObject：：序列化](reference/cobject-class.md#serialize)）。

檔也可以包含 OLE 物件。 `CDocItem`是伺服器和用戶端專案的基類。

[CDocItem](reference/cdocitem-class.md)<br/>
[COleClientItem](reference/coleclientitem-class.md)和[COleServerItem](reference/coleserveritem-class.md)的抽象基類。 衍生自的類別物件 `CDocItem` 代表檔的各部分。

## <a name="see-also"></a>另請參閱

[類別概觀](class-library-overview.md)

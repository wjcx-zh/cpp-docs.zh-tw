---
title: OLE 容器類別
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 87db824e5ab4daec15870b245ea8341be7442109
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292549"
---
# <a name="ole-container-classes"></a>OLE 容器類別

這些類別會使用容器應用程式。 兩者`COleLinkingDoc`並`COleDocument`管理的集合`COleClientItem`物件。 而不是衍生您的文件類別，從`CDocument`，您會從它衍生出來`COleLinkingDoc`或`COleDocument`，取決於您是否要支援以內嵌在您的文件中的物件的連結。

使用`COleClientItem`物件以代表從另一個文件內嵌或連結至另一個文件的文件中的每個 OLE 項目。

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
支援使用中文件內含項目。

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
用於複合文件的實作，以及基本的容器支援。 做為容器的類別衍生自`CDocItem`。 這個類別可用來當做基底類別容器文件，而且是基底類別`COleServerDoc`。

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
類別衍生自`COleDocument`所提供的基礎結構進行連結。 您應該將文件類別衍生自這個類別而不是從應用程式容器`COleDocument`如果您想要它們支援內嵌物件連結。

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
會維護 rich edit 控制項中的 OLE 用戶端項目清單。 搭配[CRichEditView](../mfc/reference/cricheditview-class.md)並[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)。

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
抽象的基底類別`COleClientItem`和`COleServerItem`。 類別的物件衍生自`CDocItem`代表文件的部分。

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
用戶端項目類別，表示要內嵌或連結的 OLE 項目之連接的用戶端的側邊。 從這個類別衍生您的用戶端項目。

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
提供用戶端存取權的項目儲存在 rich edit 控制項搭配使用時的 OLE`CRichEditView`和`CRichEditDoc`。

[COleException](../mfc/reference/coleexception-class.md)<br/>
因 OLE 處理失敗而產生的例外狀況。 容器和伺服器都使用這個類別。

## <a name="see-also"></a>另請參閱

[類別概觀](../mfc/class-library-overview.md)

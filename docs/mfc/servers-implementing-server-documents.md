---
title: 伺服器：實作伺服器文件
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
ms.openlocfilehash: 17ced1cdb0b40b13fbda68150030efde5735ba7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307909"
---
# <a name="servers-implementing-server-documents"></a>伺服器：實作伺服器文件

這篇文章說明如果您未指定應用程式精靈中的 OLE 伺服器 選項，成功實作伺服器文件時，必須採取的步驟。

#### <a name="to-define-a-server-document-class"></a>若要定義伺服器文件類別

1. 從 `COleServerDoc` 衍生您的文件類別，而不要從 `CDocument` 衍生。

1. 建立伺服器項目類別衍生自`COleServerItem`。

1. 實作`OnGetEmbeddedItem`伺服器文件類別的成員函式。

   `OnGetEmbeddedItem` 容器應用程式的使用者建立或編輯內嵌項目時呼叫。 它應該會傳回代表整個文件的項目。 這應該是物件您`COleServerItem`-衍生的類別。

1. 覆寫`Serialize`来序列化的文件內容的成員函式。 您不需要序列化的伺服器項目清單，除非您使用它們來代表文件中的原生的資料。 如需詳細資訊，請參閱 <<c0>  *實作伺服器項目*一文中[伺服器：伺服器項目](../mfc/servers-server-items.md)。

建立伺服器文件時，架構會自動註冊文件與 OLE 系統 Dll。 這可讓識別伺服器的文件的 Dll。

如需詳細資訊，請參閱 < [COleServerItem](../mfc/reference/coleserveritem-class.md)並[COleServerDoc](../mfc/reference/coleserverdoc-class.md)中*類別庫參考*。

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)<br/>
[伺服器：伺服器項目](../mfc/servers-server-items.md)<br/>
[伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)<br/>
[伺服器：實作就地編輯框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)

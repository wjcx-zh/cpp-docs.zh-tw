---
title: 伺服器：實作伺服器
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: a5c89ff1256d557ef417b9e53ce76bbf1b5d6196
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518953"
---
# <a name="servers-implementing-a-server"></a>伺服器：實作伺服器

這篇文章說明 MFC 應用程式精靈建立的視覺化編輯伺服器應用程式的程式碼。 如果您不使用應用程式精靈，這篇文章會列出您必須在其中撰寫程式碼來實作伺服器應用程式的區域。

如果您使用應用程式精靈 建立新的伺服器應用程式，它會為您提供大量的伺服器特定程式碼。 如果您要將視覺化編輯伺服器功能，加入現有的應用程式，您必須複製應用程式精靈 會提供新增必要的伺服器程式碼的其餘部分之前的程式碼。

應用程式精靈提供的伺服器程式碼分成數個類別：

- 定義伺服器資源：

  - 伺服器會編輯內嵌項目在它自己的視窗時所使用的功能表資源。

  - 使用的伺服器時作用中就地功能表和工具列資源。

  如需有關這些資源的詳細資訊，請參閱 <<c0> [ 功能表和資源： 伺服器加入](../mfc/menus-and-resources-server-additions.md)。

- 定義項目類別衍生自`COleServerItem`。 如需伺服器項目的的詳細資訊，請參閱 <<c0> [ 伺服器： 伺服器項目](../mfc/servers-server-items.md)。

- 變更的文件類別的基底類別`COleServerDoc`。 如需詳細資訊，請參閱 <<c0> [ 伺服器： 實作伺服器文件](../mfc/servers-implementing-server-documents.md)。

- 定義框架視窗類別衍生自`COleIPFrameWnd`。 如需詳細資訊，請參閱 <<c0> [ 伺服器： 實作就地框架 Windows](../mfc/servers-implementing-in-place-frame-windows.md)。

- 在 Windows 註冊資料庫中建立伺服器應用程式的項目，並向 OLE 系統中的伺服器的新執行個體。 如需本主題的資訊，請參閱 <<c0> [ 註冊](../mfc/registration.md)。

- 初始化和啟動伺服器應用程式。 如需本主題的資訊，請參閱 <<c0> [ 註冊](../mfc/registration.md)。

如需詳細資訊，請參閱 < [COleServerItem](../mfc/reference/coleserveritem-class.md)， [COleServerDoc](../mfc/reference/coleserverdoc-class.md)，並[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)中*類別庫參考*。

## <a name="see-also"></a>另請參閱

[伺服器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)<br/>
[功能表和資源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[註冊](../mfc/registration.md)


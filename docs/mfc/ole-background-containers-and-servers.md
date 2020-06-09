---
title: OLE 背景：容器和伺服器
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: 7c3130ab9d8dff6551ef0ecbec43e5422dbdc4c4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617902"
---
# <a name="ole-background-containers-and-servers"></a>OLE 背景：容器和伺服器

容器應用程式是一種應用程式，可以將內嵌或連結項目加入到本身的文件中。 由容器應用程式管理的檔必須能夠儲存和顯示 OLE 檔元件，以及應用程式本身所建立的資料。 容器應用程式也必須允許使用者在必要時啟用伺服器應用程式，以插入新專案或編輯現有的專案。 容器應用程式的使用者介面需求會列在 [[容器：使用者介面問題](containers-user-interface-issues.md)] 一文中。

伺服器應用程式或元件應用程式是一種應用程式，可以建立可供容器應用程式使用的 OLE 檔元件。 伺服器應用程式通常支援將資料拖放或複製到剪貼簿，讓容器應用程式可以插入資料做為內嵌或連結的專案。 應用程式可以是容器和伺服器。

大部分的伺服器都是獨立應用程式或完整伺服器;它們可以當做獨立應用程式來執行，或由容器應用程式啟動。 「袖珍伺服器」是一種特殊類型的伺服器應用程式，只能由容器啟動。 它無法以獨立應用程式的形式執行。 Microsoft Draw 和 Microsoft Graph 伺服器是 miniservers 的範例。

容器和伺服器不會直接通訊。 相反地，它們會透過 OLE 系統動態連結程式庫（DLL）進行通訊。 這些 Dll 會提供容器和伺服器呼叫的函式，而容器和伺服器則提供 Dll 所呼叫的回呼函式。

使用這種通訊方式，容器不需要知道伺服器應用程式的執行詳細資料。 它允許容器接受任何伺服器所建立的專案，而不需要定義可用於執行工作的伺服器類型。 因此，容器應用程式的使用者可以利用未來的應用程式和資料格式。 如果這些新的應用程式是 OLE 元件，則複合檔案將能夠併入這些應用程式所建立的專案。

## <a name="see-also"></a>另請參閱

[OLE 背景](ole-background.md)<br/>
[OLE 背景：MFC 實作](ole-background-mfc-implementation.md)<br/>
[容器](containers.md)<br/>
[伺服器](servers.md)<br/>
[容器：用戶端項目](containers-client-items.md)<br/>
[伺服器：伺服器項目](servers-server-items.md)

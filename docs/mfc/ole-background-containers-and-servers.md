---
title: OLE 背景： 容器和伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23aa5e4c13e8049a2240462dab1c5b68bfb514f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436932"
---
# <a name="ole-background-containers-and-servers"></a>OLE 背景：容器和伺服器

容器應用程式是一種應用程式，可以將內嵌或連結項目加入到本身的文件中。 管理容器應用程式的文件必須能夠儲存及顯示 OLE 文件元件，以及建立應用程式本身的資料。 容器應用程式也必須允許插入新項目或編輯現有的項目，藉由啟用伺服器應用程式時所需的使用者。 文章中會列出容器應用程式的使用者介面需求[容器： 使用者介面問題](../mfc/containers-user-interface-issues.md)。

伺服器應用程式或元件應用程式是可以建立容器應用程式使用的 OLE 文件元件的應用程式。 伺服器應用程式通常會支援拖放作業或是將其資料複製到剪貼簿，使容器應用程式可以插入的資料做為內嵌或連結的項目。 應用程式可以同時為容器和伺服器。

大部分的伺服器是獨立的應用程式或完整伺服器;它們是可當做獨立應用程式來執行，或可由容器應用程式啟動。 迷你伺服程式是一種特殊的伺服器應用程式，可以只由容器啟動。 它無法執行獨立的應用程式。 Microsoft 繪製和 Microsoft Graph 的伺服器是迷你伺服程式的範例。

容器和伺服器不直接通訊。 相反地，他們透過 OLE 系統動態連結程式庫 (DLL) 通訊。 這些 Dll 提供容器和伺服器呼叫，函式和容器和伺服器提供的 Dll 呼叫的回呼函式。

使用此種通訊的方式，容器不需要知道伺服器應用程式的實作詳細資料。 它可讓容器以接受任何伺服器所建立，而不需要定義的它可以運作的伺服器類型的項目。 如此一來，容器應用程式的使用者可以利用未來的應用程式和資料格式。 如果這些新的應用程式是 OLE 元件，在複合文件會無法將這些應用程式所建立的項目。

## <a name="see-also"></a>另請參閱

[OLE 背景](../mfc/ole-background.md)<br/>
[OLE 背景：MFC 實作](../mfc/ole-background-mfc-implementation.md)<br/>
[容器](../mfc/containers.md)<br/>
[伺服器](../mfc/servers.md)<br/>
[容器：用戶端項目](../mfc/containers-client-items.md)<br/>
[伺服器：伺服器項目](../mfc/servers-server-items.md)


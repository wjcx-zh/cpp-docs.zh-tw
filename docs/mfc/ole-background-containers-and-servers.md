---
title: "OLE 背景： 容器和伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3c6f3c15b0ea398ec621ba5f6e34a9fb6e0aae8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ole-background-containers-and-servers"></a>OLE 背景：容器和伺服器
容器應用程式是一種應用程式，可以將內嵌或連結項目加入到本身的文件中。 容器應用程式管理的文件必須能夠儲存和顯示 OLE 文件元件，以及應用程式本身所建立的資料。 容器應用程式也必須允許使用者插入新項目，或啟動時所需的伺服器應用程式來編輯現有的項目。 文件中列出的容器應用程式的使用者介面需求[容器： 使用者介面問題](../mfc/containers-user-interface-issues.md)。  
  
 伺服器應用程式或元件應用程式是應用程式所建立的 OLE 文件元件使用容器應用程式。 伺服器應用程式通常會支援拖放作業或是其資料複製到剪貼簿，使容器應用程式可以將插入的資料做為內嵌或連結項目。 應用程式可以同時為容器和伺服器。  
  
 大部分的伺服器是獨立應用程式或完整伺服器。它們可以做為獨立的應用程式會執行，或由容器應用程式來啟動。 迷你伺服程式是一種特殊的伺服器應用程式，可以只由容器啟動。 不能執行獨立的應用程式。 Microsoft 繪製和 Microsoft Graph 伺服器是迷你伺服程式的範例。  
  
 容器和伺服器不直接通訊。 相反地，它們透過 OLE 系統動態連結程式庫 (DLL) 通訊。 這些 Dll 提供容器和伺服器呼叫的函式和容器和伺服器提供的 Dll 呼叫的回呼函式。  
  
 使用這種通訊時，容器不需要知道伺服器應用程式的實作詳細資料。 它可讓容器以接受任何伺服器所建立，而不必定義類型的伺服器可以使用的項目。 如此一來，容器應用程式的使用者可以利用未來的應用程式和資料格式。 如果這些新的應用程式是 OLE 元件，則複合文件會可以將這些應用程式所建立的項目。  
  
## <a name="see-also"></a>請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [OLE 背景： MFC 實作](../mfc/ole-background-mfc-implementation.md)   
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)   
 [容器： 用戶端項目](../mfc/containers-client-items.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)


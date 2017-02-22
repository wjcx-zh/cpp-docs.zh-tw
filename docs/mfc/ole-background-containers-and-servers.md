---
title: "OLE 背景：容器和伺服器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "容器, OLE 容器應用程式"
  - "全伺服程式"
  - "OLE 容器, 容器應用程式"
  - "OLE 全伺服應用程式"
  - "OLE 伺服器應用程式, 關於伺服器應用程式"
  - "OLE 伺服器應用程式, 迷你伺服應用程式"
  - "伺服器應用程式"
  - "伺服器應用程式, 與容器通訊"
  - "伺服器應用程式, 已定義的"
  - "伺服器應用程式, 全伺服程式和迷你伺服程式比較"
  - "伺服器應用程式, 需求"
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 背景：容器和伺服器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

容器應用程式可以合併內嵌或連結的項目加入至文件的應用程式。  由容器應用程式的文件 Managed 必須能夠儲存和顯示 OLE 文件組件以及應用程式所建立的資料。  容器應用程式也必須授與使用者插入新項目或透過啟動伺服器應用程式編輯現有的項目，如果必要。  容器應用程式的使用者介面 \(UI\) 要求在 [容器:使用者介面問題](../mfc/containers-user-interface-issues.md)一文清單。  
  
 伺服器應用程式或元件的應用程式可以建立 OLE 文件組件供容器應用程式使用的應用程式。  通常伺服器應用程式支援拖放或複製到剪貼簿的資料，讓容器應用程式可以插入資料做為內嵌或連結的項目。  應用程式可以是容器和伺服器。  
  
 大部分伺服器是獨立應用程式或全伺服器;它們以獨立應用程式或可由容器應用程式啟動。  miniserver 是容器來啟動伺服器應用程式的特定型別。  它不能當做獨立的應用程式。  Microsoft 繪製和 Microsoft Graph 伺服器是 miniservers 的範例。  
  
 容器和伺服器不直接通訊。  相反地，會透過 OLE 系統動態連結程式庫 \(DLL\) \(DLL\) 進行通訊。  這些 DLL 函式提供容器和伺服器呼叫和容器和伺服器提供 DLL 呼叫的回呼函式。  
  
 使用這個通訊方式，容器不需要知道伺服器應用程式的實作詳細資料。  它可讓容器接受所有伺服器所建立的項目，而不需要定義一起使用可以伺服器類型。  因此，容器應用程式的使用者可以利用未來應用程式和資料格式。  如果這些新的應用程式是 OLE 元件，則複合文件可以結合這些應用程式建立的項目。  
  
## 請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [OLE 背景：MFC 實作](../mfc/ole-background-mfc-implementation.md)   
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)   
 [容器：用戶端項目](../mfc/containers-client-items.md)   
 [伺服器：伺服器項目](../mfc/servers-server-items.md)
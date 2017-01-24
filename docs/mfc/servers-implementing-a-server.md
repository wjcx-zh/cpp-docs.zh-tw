---
title: "伺服器：實作伺服器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE 伺服器應用程式, 實作 OLE 伺服器"
  - "伺服器, 實作"
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 伺服器：實作伺服器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明 MFC 應用程式精靈為視覺化編輯伺服器應用程式所建立的程式碼。  如果您不使用應用程式精靈，本文列出您必須撰寫程式碼實作伺服器應用程式的位置。  
  
 如果您使用應用程式精靈建立新的伺服器應用程式，它會提供大量的伺服器特定程式碼。  如果您將視覺化編輯伺服程式功能加入至現有的應用程式，您必須重複應用程式精靈會將在加入其餘必要的伺服器端程式碼之前提供的程式碼。  
  
 應用程式精靈提供的伺服器端程式碼分成數個分類：  
  
-   定義伺服器資源：  
  
    -   當伺服器在其視窗編輯其內嵌視窗時所使用的功能表資源。  
  
    -   當伺服器就地使用時使用的功能表和工具列資源。  
  
     如需這些資源的詳細資訊，請參閱 [功能表和資源：伺服器加入](../mfc/menus-and-resources-server-additions.md)。  
  
-   定義衍生自 `COleServerItem`的項目類別。  如需在伺服器上項目的詳細資訊，請參閱 [伺服器：伺服器項目](../mfc/servers-server-items.md)。  
  
-   將文件類別的基底類別變更為 `COleServerDoc`。  如需詳細資訊，請參閱 [伺服器：實作伺服器資料](../mfc/servers-implementing-server-documents.md)。  
  
-   定義從 `COleIPFrameWnd`衍生的框架視窗類別。  如需詳細資訊，請參閱 [伺服器：實作就地框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)。  
  
-   建立伺服器應用程式的項目在 Windows 系統註冊資料庫和登錄伺服器的新執行個體的 OLE 系統。  如需關於此主題的詳細資訊，請參閱 [Registration](../mfc/registration.md)。  
  
-   初始化和啟動伺服器應用程式。  如需關於此主題的詳細資訊，請參閱 [Registration](../mfc/registration.md)。  
  
 如需詳細資訊，請參閱 *Class Library Reference* 中的 [COleServerItem](../mfc/reference/coleserveritem-class.md)、[COleServerDoc](../mfc/reference/coleserverdoc-class.md) 和 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)。  
  
## 請參閱  
 [伺服器](../mfc/servers.md)   
 [容器](../mfc/containers.md)   
 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [註冊](../mfc/registration.md)
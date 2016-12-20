---
title: "MFC 中的 OLE | Microsoft Docs"
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
  - "應用程式 [OLE], 關於 OLE"
  - "MFC [C++], OLE 和"
  - "OLE [C++]"
  - "OLE 應用程式 [C++], 關於 OLE"
  - "OLE 元件物件模型 (COM)"
  - "OLE 容器, 關於 OLE"
  - "OLE 項目"
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 中的 OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用 MFC，這些文章說明 OLE 程式設計的基本概念。  MFC 提供簡易的方法覆寫使用 OLE 的程式:  
  
-   使用 OLE 視覺化編輯 \(就地啟用\)。  
  
-   以 OLE 容器或伺服器。  
  
-   實作拖放功能。  
  
-   使用日期和時間資料。  
  
-   處理 MFC 模組狀態資料，包括匯出 DLL 函式進入點， OLE\/COM 介面進入點和視窗程序進入點。  
  
 您也可以使用 [Automation](../mfc/automation.md) 或 [遠端自動化](../mfc/remote-automation.md) 從程式操作其他程式。  
  
> [!NOTE]
>  詞彙 OLE 表示技術與連結和內嵌，包括 OLE 容器、OLE 伺服器、OLE 項目、就地編輯啟動 \(或的視覺化\)，追蹤、拖放和功能表合併。  詞彙現用適用於元件物件模型 \(COM\) \(COM\) 和 COM 架構物件 \(例如 ActiveX 控制項。  OLE Automation 現在稱為 Automation。  
  
## 本章節內容  
 [OLE 背景](../mfc/ole-background.md)  
 討論 OLE 並提供如何概念的相關資訊。  
  
 [啟動](../mfc/activation-cpp.md)  
 在編輯描述啟用角色 OLE 項目。  
  
 [容器](../mfc/containers.md)  
 提供如何使用容器在 OLE。  
  
 [資料物件和資料來源](../mfc/data-objects-and-data-sources-ole.md)  
 連結主題所討論的主題使用 `COleDataObject` 和 `COleDataSource` 類別。  
  
 [拖放](../mfc/drag-and-drop-ole.md)  
 與 OLE 討論使用複製和貼上。  
  
 [OLE 功能表和資源](../mfc/menus-and-resources-ole.md)  
 說明功能表和資源的使用在 MFC OLE 文件應用程式。  
  
 [登錄](../mfc/registration.md)  
 討論伺服器安裝及使用。  
  
 [伺服程式](../mfc/servers.md)  
 描述如何建立 OLE 項目 \(或元件\) 供容器應用程式使用。  
  
 [追蹤器](../mfc/trackers.md)  
 提供 `CRectTracker` 類別的資訊，提供圖形介面可讓使用者與 OLE 用戶端項目互動。  
  
## 相關章節  
 [連接點](../mfc/connection-points.md)  
 說明如何實作連接點 \(先前稱為 OLE 連接點\) 使用 MFC 類別 `CCmdTarget` ，以及 `CConnectionPoint`。  
  
 [容器\/伺服器 COM 元件](../mfc/containers-advanced-features.md)  
 說明必要步驟合併任意進階功能加入至現有的容器應用程式中。  
  
 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 描述使用 OLE，不使用 MFC。  
  
## 請參閱  
 [概念](../mfc/mfc-concepts.md)
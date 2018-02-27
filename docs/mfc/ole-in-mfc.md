---
title: "MFC 中的 OLE |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d13baf7960b329e56cfce24011f4c15599cdda8b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="ole-in-mfc"></a>MFC 中的 OLE
這些文件說明使用 MFC 的 OLE 程式設計基本概念。 MFC 提供最簡易的方法撰寫使用 OLE 的程式：  
  
-   使用 OLE 視覺化編輯 (就地啟用)。  
  
-   做為 OLE 容器或伺服器使用。  
  
-   實作拖放功能。  
  
-   使用日期和時間資料。  
  
-   管理 MFC 模組的狀態資料，包括匯出的 DLL 函式進入點、OLE/COM 介面進入點和視窗程序進入點。  
  
 您也可以使用[自動化](../mfc/automation.md)。  
  
> [!NOTE]
>  OLE 一詞表示與連結和內嵌相關的技術，包括 OLE 容器、OLE 伺服器、OLE 項目、就地啟用 (或視覺化編輯)、追蹤器、拖放和功能表合併。 「作用中」一詞適用於元件物件模型 (COM) 和 COM 架構的物件，例如 ActiveX 控制項。 OLE Automation 現在稱為 Automation。  
  
## <a name="in-this-section"></a>本節內容  
 [OLE 背景](../mfc/ole-background.md)  
 討論 OLE 並提供運作方式相關的概念資訊。  
  
 [啟動](../mfc/activation-cpp.md)  
 說明編輯 OLE 項目時的角色啟用。  
  
 [容器](../mfc/containers.md)  
 提供在 OLE 中使用容器的連結。  
  
 [資料物件和資料來源](../mfc/data-objects-and-data-sources-ole.md)  
 提供討論使用 `COleDataObject` 和 `COleDataSource` 類別的主題的連結。  
  
 [拖放](../mfc/drag-and-drop-ole.md)  
 討論使用 OLE 複製和貼上。  
  
 [OLE 功能表和資源](../mfc/menus-and-resources-ole.md)  
 說明在 MFC OLE 文件應用程式中功能表和資源的使用。  
  
 [註冊](../mfc/registration.md)  
 討論伺服器的安裝和初始化。  
  
 [伺服器](../mfc/servers.md)  
 說明如何建立 OLE 項目 (或元件) 供容器應用程式使用。  
  
 [追蹤器](../mfc/trackers.md)  
 提供 `CRectTracker` 類別的相關資訊，該類別提供圖形介面，可讓使用者與 OLE 用戶端項目互動。  
  
## <a name="related-sections"></a>相關章節  
 [連接點](../mfc/connection-points.md)  
 說明如何使用 MFC 類別 `CCmdTarget` 和 `CConnectionPoint` 實作連接點 (先前稱為 OLE 連接點)。  
  
 [容器/伺服器 COM 元件](../mfc/containers-advanced-features.md)  
 說明將選擇性的進階功能併入現有的容器應用程式中的必要步驟。  
  
 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 說明使用 OLE 而不使用 MFC。  
  
## <a name="see-also"></a>請參閱  
 [概念](../mfc/mfc-concepts.md)


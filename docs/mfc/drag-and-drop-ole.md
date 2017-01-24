---
title: "拖放 (OLE) | Microsoft Docs"
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
  - "拖放 [C++]"
  - "拖放 [C++], 關於 OLE 拖放"
  - "檔案管理員拖放支援"
  - "OLE 應用程式, 拖放"
  - "OLE 拖放"
  - "OLE 伺服器應用程式, 拖放"
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 拖放功能是複製並貼上資料的主要捷徑。  當您使用剪貼簿複製或貼上資料時，需要幾個步驟。  您選取的資料，從 **編輯** 功能表按一下 **Cut** 或 **Copy**，移動到目的檔案，視窗或應用程式中，將游標放置於目標地，然後從 **編輯** 功能表按一下 **貼上**。  
  
 OLE 拖放與文件管理員拖放機制不同，它只能處理檔名且特別設計來傳遞檔名給應用程式。  OLE 拖放更為泛用。  它允許您拖放能在剪貼簿上放置的資料。  
  
 當您使用 OLE 拖放時，您從工作流程移除兩個步驟。  您從來源視窗 \(置放來源\) 選取資料，將它拖曳至想要的目的 \(置放目標\)，並透過放開滑鼠按鈕放下。  此作業消除對功能表的需要，且比複製\/貼上操作流程更快。  唯一的要求是拖曳來源和置放目標必須為開啟且至少部分顯示在螢幕上。  
  
 使用 OLE 拖放功能，可以從一個位置和資料夾內，不同資料夾之間，或應用程式之間傳輸資料。  它可以在容器或伺服器應用程式實做，且所有應用程式可以是置放來源，置放目標或兩者都是。  如果應用程式實作置放來源和置放目標支援，允許在子視窗之間，或在一個視窗中拖放。  此功能可讓應用程式更容易使用。  
  
 如果您只想要使用 OLE 的拖放功能，請參閱 [拖放:自訂](../mfc/drag-and-drop-customizing.md)。  可以使用在該文件說明的技巧進行非 OLE 應用程式成為置放來源。  [拖放:實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md) 文件描述如何實作置放目標支援 OLE 和非 OLE 應用程式。  檢查 MFC OLE 範例 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md)也會很有用。  
  
 如果您還沒有閱讀 [資料物件和資料來源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 文件系列，您可能會想要現在閱讀。  這些文章說明資料傳輸的基本概念，以及如何在您的應用程式實作它。  
  
 如需拖放功能的詳細資訊，請參閱：  
  
-   [拖放：實作置放來源](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [拖放：實作置放目標](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [拖放：自訂](../mfc/drag-and-drop-customizing.md)  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [資料物件和資料來源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)
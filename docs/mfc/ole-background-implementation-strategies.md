---
title: "OLE 背景：實作策略 | Microsoft Docs"
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
  - "應用程式 [OLE], 實作 OLE"
  - "OLE [C++], 開發策略"
  - "OLE 應用程式 [C++], 實作 OLE"
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 背景：實作策略
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據您的應用程式，則會加上 OLE 支援四種可能的實作策略：  
  
-   撰寫新的應用程式。  
  
     這種情況通常需要最少工作。  您執行 MFC 應用程式精靈並選擇進階功能或複合文件支援建立基本架構應用程式。  如需這些選項的詳細資訊以及在做什麼，請參閱本文件的 [建立 MFC EXE 程式](../mfc/reference/mfc-application-wizard.md)。  
  
-   您有程式是以不支援 OLE 的MFC 程式庫版本 2.0 \(含\) 以上版本所撰寫的。  
  
     如前所述建立 MFC 應用程式精靈建立新的應用程式，然後複製並貼上新應用程式的程式碼加入至現有的應用程式。  對於伺服器、容器或自動化應用程式中運作。  為這個策略的範例參閱 MFC [Scribble](../top/visual-cpp-samples.md) 範例。  
  
-   您可以實作 OLE 1.0 版支援的 MFC 程式庫程式。  
  
     為這個轉換策略，請參閱 [MFC 技術提示 41](../mfc/tn041-mfc-ole1-migration-to-mfc-ole-2.md) 。  
  
-   您有尚未寫入使用 Microsoft Foundation Class，而且可以或不可以實作 OLE 支援的應用程式。  
  
     這種情況需要大部分的工作。  一種方法是建立新的應用程式，在第一項策略，然後複製並貼上您現有的程式碼貼入其中。  如果現有的程式碼撰寫 C\#，則您可能需要修改，因此它可以當作 C\+\+ 程式碼編譯。  如果您的 C\# 程式碼呼叫 Windows API，則您不需要變更它使用 Microsoft Foundation Class。  這個方法可能會要求您的程式某些變更結構支援版本使用文件\/檢視架構 2.0 而 Microsoft Foundation Classes。  如需結構的詳細資訊，請參閱 [Technical Note 25](../mfc/tn025-document-view-and-frame-creation.md)。  
  
 一旦決定了策略，您應該閱讀 [容器](../mfc/containers.md) 或 [伺服器](../mfc/servers.md) 文章 \(視您寫入\) 的應用程式類型或檢查範例程式或兩者。  MFC OLE、MFC 範例 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 分別顯示如何實作容器和伺服器的各個層面。  在這些文件中的幾個不同點，您將會在這些範例中參考的某些函式，如討論的技術之範例。  
  
## 請參閱  
 [OLE 背景](../mfc/ole-background.md)   
 [容器：實作容器](../mfc/containers-implementing-a-container.md)   
 [伺服器：實作伺服器](../mfc/servers-implementing-a-server.md)   
 [MFC 應用程式精靈](../mfc/reference/mfc-application-wizard.md)
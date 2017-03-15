---
title: "功能表和資源 (OLE) | Microsoft Docs"
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
  - "應用程式 [OLE], 功能表和資源"
  - "容器 [C++], OLE 容器應用程式"
  - "就地啟用, OLE 功能表和資源"
  - "功能表 [C++], OLE 文件應用程式"
  - "OLE 應用程式 [C++], 功能表和資源"
  - "OLE 容器, 功能表和資源"
  - "OLE 功能表和資源"
  - "OLE 伺服器應用程式, 功能表和資源"
  - "OLE 視覺化編輯伺服器"
  - "伺服器應用程式, OLE 功能表和資源"
  - "狀態列, OLE 文件應用程式"
  - "字串編輯, 視覺化編輯應用程式"
  - "字串資料表, 視覺化編輯應用程式"
  - "工具列 [C++], OLE 文件應用程式"
  - "視覺化編輯, 應用程式功能表和資源"
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 功能表和資源 (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文件的此群組說明功能表和資源的使用在 MFC OLE 文件應用程式。  
  
 編輯功能表中的其他需求和其他資源的 OLE 視覺化提供 OLE 文件應用程式，因為容器和伺服器的方式 \(Component\) 應用程式可以開始使用。  例如，全伺服應用在下可以執行任何這三種方式:  
  
-   單機  
  
-   就地，提供編輯在容器內的項目。  
  
-   提供編輯其容器之外內容的項目，開啟，通常在另一個視窗中。  
  
 這需要三個不同功能表配置，應用程式的每個可能的方式。  快速鍵對應表為每個新的方式也是必要的。  容器應用程式不一定支援就地啟動;如果是，它需要新的功能表結構與關聯的快速鍵對應表。  
  
 就地啟動要求容器和伺服器應用程式必須為功能表、工具列和狀態列空間交涉。  必須瞭解此設計任何資源。  這篇文章 [功能表和資源:功能表合併。](../mfc/menus-and-resources-menu-merging.md) 詳細包括主題。  
  
 由於這些問題， OLE 文件應用程式以應用程式精靈可能有四種不同功能表和快速鍵對應表資源。  這些原因如下使用:  
  
|資源名稱|用法|  
|----------|--------|  
|**IDR\_MAINFRAME**|使用在 MDI 應用程式中，如果檔案未開啟，或者在 SDI 應用程式中開啟檔案。  這是用於非 OLE 應用程式的標準功能表。|  
|**IDR\_\<project\>TYPE**|使用在 MDI 應用程式中，如果檔案已經開啟。  使用，當應用程式是以獨立。  這是用於非 OLE 應用程式的標準功能表。|  
|**IDR\_\<project\>TYPE\_SRVR\_IP**|使用由伺服器或容器，當物件開啟準備就緒。|  
|**IDR\_\<project\>TYPE\_SRVR\_EMB**|使用由伺服器應用程式，如果物件開啟，而不使用就地啟動。|  
  
 這些資源名稱中的每個物件都代表一個功能表，然後，一般而言，快速鍵對應表。  一個類似的計劃應該用於不以應用程式精靈建立 MFC 應用程式。  
  
 下列文件說明主題與容器，伺服器和功能表合併必要相關實作就地啟動:  
  
-   [功能表和資源：容器新增](../mfc/menus-and-resources-container-additions.md)  
  
-   [功能表和資源：伺服器新增](../mfc/menus-and-resources-server-additions.md)  
  
-   [功能表和資源：功能表合併](../mfc/menus-and-resources-menu-merging.md)  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)
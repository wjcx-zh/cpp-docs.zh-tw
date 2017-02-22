---
title: "伺服器 | Microsoft Docs"
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
  - "全伺服程式"
  - "迷你伺服程式"
  - "OLE 伺服器應用程式"
  - "OLE 伺服器應用程式, 啟動"
  - "OLE 伺服器應用程式, 伺服器類型"
  - "伺服器應用程式"
  - "伺服器"
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 伺服器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

伺服器應用程式 \(或元件應用程式\) 會將 OLE 項目 \(或元件\) 供容器應用程式使用。  視覺化編輯伺服器應用程式也支援視覺化編輯或就地啟動。  OLE 伺服器另一表單是 [Automation 伺服器](../mfc/automation-servers.md)。  某些伺服器應用程式支援內嵌項目只建立;其他支援內嵌和連結項目的建立。  一些支援只連接，不過，這很罕見。  表示使用者想要編輯項目時，所有伺服器應用程式必須由容器應用程式支援啟動。  應用程式可以是容器和伺服器。  換句話說，它可將資料加入至文件中建立可合併成項目到其他應用程式的文件中的資料。  
  
 miniserver 可能由容器才啟動伺服器應用程式的特定型別。  Microsoft 繪製和 Microsoft Graph 是 miniservers 的範例。  miniserver 不以將文件儲存為檔案在磁碟上。  相反地，它會讀取資料並將項目寫入到屬於容器的文件。  因此， miniserver 只支援內嵌，而連接。  
  
 全伺服器可以當做獨立的應用程式或由容器應用程式啟動。  全伺服器可能以將文件儲存為檔案在磁碟上。  它可能只支援內嵌，內嵌和連結或只連接。  容器應用程式的使用者可以選取伺服器的剪下或複製命令及容器的貼上命令建立內嵌項目。  連結的項目可以選取伺服器上的複製命令及容器的貼上連結命令建立。  或者，使用插入物件對話方塊，使用者可以建立內嵌或連結的項目。  
  
 下表摘要說明伺服器的不同類型的特性:  
  
### 伺服器特性  
  
|伺服器上的型別|支援多個執行個體。|項目的每個文件|文件的每個執行個體|  
|-------------|---------------|-------------|---------------|  
|Miniserver|有|1|1|  
|SDI 全伺服器|有|1 \(如果連接支援， 1 或更\)|1|  
|MDI 全伺服器|沒有 \(不需要\)|1 \(如果連接支援， 1 或更\)|0 或更多|  
  
 在一個以上的容器可用來編輯內嵌或連結項目的情況下，伺服器應用程式應該同時支援多個容器。  如果伺服器是 SDI 應用程式 \(或與對話方塊介面的 miniserver\)，伺服器的多個執行個體必須能夠同時執行。  這樣可以讓應用程式的個別執行個體處理每個容器要求。  
  
 如果伺服器是 MDI 應用程式，可以建立新的 MDI 子視窗，每次容器需要編輯項目。  如此一來，應用程式的單一執行個體可以支援多個容器。  
  
 您的伺服器應用程式必須呼叫這個 OLE 系統 DLL 要執行的動作，如果伺服器的執行個體已經在執行，而其他容器要求其服務:它應該啟動伺服器上建立新的執行個體或指示所有容器的要求至伺服器上的執行個體。  
  
 如需詳細資訊在伺服器，請參閱:  
  
-   [伺服程式：實作一個伺服程式](../mfc/servers-implementing-a-server.md)  
  
-   [伺服器:實作伺服器資料](../mfc/servers-implementing-server-documents.md)  
  
-   [伺服器:實作就地框架視窗](../mfc/servers-implementing-in-place-frame-windows.md)  
  
-   [伺服器:伺服器項目](../mfc/servers-server-items.md)  
  
-   [伺服器:使用者介面問題](../mfc/servers-user-interface-issues.md)  
  
## 請參閱  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [容器：進階功能](../mfc/containers-advanced-features.md)   
 [功能表和資源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [註冊](../mfc/registration.md)   
 [Automation 伺服程式](../mfc/automation-servers.md)
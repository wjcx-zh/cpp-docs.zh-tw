---
title: "MFC 網際網路程式設計工作 | Microsoft Docs"
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
  - "網際網路應用程式, 第一步"
  - "網際網路應用程式, 使用者入門"
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# MFC 網際網路程式設計工作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本節包含加入網際網路支援至您的應用程式的詳細步。  主題包含如何使用 MFC 類別網際網路啟用您的現有應用程式和如何將主動式文件支援加入至現有的 COM 元件。  您是否想要建立更新股價、匹茲堡的橄欖球分數和最新的南極洲溫度的資料的文件?  Microsoft 提供幾種技巧可以協助您在網際網路進行這件事。  
  
 Active 技術包括 ActiveX 控制項 \(先前稱為 OLE automation 控制項\) 和 Active 文件；可擷取和儲存 WinInet 跨網際網路檔案；而且有效率資料下載的非同步標記。  Visual C\+\+ 提供精靈用起始應用程式協助您快速入門。  如需這些技術的簡介，請參閱 [MFC 網際網路程式設計的基本概念。](../mfc/mfc-internet-programming-basics.md) 和 [MFC COM](../mfc/mfc-com.md)。  
  
 您是否總是要 FTP 檔案，但是未學習 Winsock 和網路程式設計通訊協定?  WinInet 類別封裝這些通訊協定，提供您簡單的可讓您用來在網際網路上撰寫客戶端應用程式使用 HTTP、FTP 和 gopher 下載檔案的一組函式。  您可以使用 WinInet 搜尋您的硬碟的環境儲存目錄或整個世界。  您可以以透明方式收集不同型別的資料，並將其展示給聯合的使用者介面。  
  
 您是否有下載大量的資料?  非同步標記為大型物件進行轉換列提供 COM \(元件物件模型 \(Component Object Model，COM\) 方案。  WinInet 也可以非同步使用。  
  
 下表描述您可以使用這些技術的一些事項。  
  
|您有|您想要|您應該|  
|--------|---------|---------|  
|網頁伺服器|追蹤記錄檔和詳細資訊的 URL 要求。|寫入一個篩選條件、註冊事件和 URL 要求對應的通知。|  
|Web 瀏覽器|提供動態內容。|建立 ActiveX 控制項和現用文件。|  
|以文件為基礎的應用程式。|加入支援 FTP 檔案。|使用 WinInet 或非同步標記。|  
  
 請參閱下列主題以取得詳細資訊讓您開始：  
  
-   [應用程式設計選擇](../mfc/application-design-choices.md)  
  
-   [撰寫 MFC 應用程式](../mfc/writing-mfc-applications.md)  
  
-   [網際網路上的 ActiveX 控制項](../mfc/activex-controls-on-the-internet.md)  
  
-   [升級現有的 ActiveX 控制項](../mfc/upgrading-an-existing-activex-control.md)  
  
-   [網際網路上的主動式文件](../mfc/active-documents-on-the-internet.md)  
  
-   [網際網路上的非同步 Moniker](../mfc/asynchronous-monikers-on-the-internet.md)  
  
-   [測試網際網路應用程式](../mfc/testing-internet-applications.md)  
  
-   [網際網路安全性](../mfc/internet-security-cpp.md)  
  
## 請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [依工作分類的網際網路資訊](../mfc/internet-information-by-task.md)
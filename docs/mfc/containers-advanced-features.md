---
title: "容器：進階功能 | Microsoft Docs"
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
  - "容器/伺服器應用程式 [C++]"
  - "容器 [C++], 進階功能"
  - "容器 [C++], 容器應用程式"
  - "容器 [C++], 內嵌 OLE 物件的連結"
  - "內嵌物件 [C++]"
  - "連結 [C++], 內嵌 OLE 物件的"
  - "OLE 容器, 進階功能"
  - "OLE 控制項, 容器"
  - "伺服器/容器應用程式"
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器：進階功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明的必要步驟合併任意進階功能加入至現有的容器應用程式中。  這些特性包括：  
  
-   [為容器和伺服器的應用程式](#_core_creating_a_container.2f.server_application)  
  
-   [內嵌物件的一個 OLE 連結。](#_core_links_to_embedded_objects)  
  
##  <a name="_core_creating_a_container.2f.server_application"></a> 建立容器\/伺服器應用程式。  
 容器\/伺服器應用程式為容器和伺服器的應用程式。  視窗的 Microsoft Word 是這樣的範例。  您可以在其他應用程式中嵌入文件視窗的文字，然後，您也可以在 Windows 文件的文字內嵌項目。  修改您的容器應用程式處理序是容器和全伺服器 \(您無法建立組合容器\/miniserver 應用程式\) 類似於建立的完整伺服器處理序。  
  
 這篇文章 [伺服器:實作伺服器](../mfc/servers-implementing-a-server.md) 列出需要的工作實作伺服器應用程式。  如果轉換容器應用程式到容器\/伺服器應用程式，則您必須執行一些相同的工作，將程式碼加入至容器。  以下列出重要的考量:  
  
-   容器程式碼由應用程式精靈建立已經初始化 OLE 子系統。  您不需要變更或加入該支援。  
  
-   文件類別的基底類別是 `COleDocument`，變更基底類別加入至 `COleServerDoc`。  
  
-   當伺服器使用就地編輯時，請覆寫 `COleClientItem::CanActivate` 避免編輯項目。  
  
     例如， MFC OLE 範例 [OCLIENT](../top/visual-cpp-samples.md) 內嵌了容器\/伺服器應用程式建立項目。  您開啟 OCLIENT 應用程式，而且該項目由您的容器\/伺服器應用程式建立的就地編輯。  當編輯應用程式的項目時，您決定要內嵌 MFC OLE 範例[HIERSVR](../top/visual-cpp-samples.md)建立的項目。  若要這樣做，您無法使用就地啟動。  您必須完全開啟 HIERSVR 啟動這個項目。  因為 MFC 程式庫不支援這個 OLE 功能，覆寫 `COleClientItem::CanActivate` 可讓您檢查條件並防止在應用程式中可能的執行階段錯誤。  
  
 如果您建立新的應用程式並想要它當做容器\/伺服器應用程式，請選取 OLE 選項對話方塊的選項在應用程式精靈和這個支援將會自動建立。  如需詳細資訊，請參閱文件 [概觀:建立 ActiveX 控制項容器](../mfc/reference/creating-an-mfc-activex-control-container.md)。  如需 MFC 範例的詳細資訊，請參閱 MFC 範例。  
  
 請注意您無法插入 MDI 應用程式至本身。  為容器\/伺服器的應用程式不能插入至本身，除非它是 SDI 應用程式。  
  
##  <a name="_core_links_to_embedded_objects"></a> 內嵌物件的連結  
 內嵌物件功能的連結可讓使用者建立一個 OLE 連結的資料加入至容器應用程式內的內嵌物件。  例如，建立包含內嵌報表的文書處理器的文件。  如果您的內嵌物件，它的應用程式支援連結可能貼上連結至文書處理器之資料的報表。  這項功能可讓您的應用程式使用報表中包含的資訊，而不需要知道放置初始取得的文書處理器。  
  
#### 在應用程式的內嵌物件連接  
  
1.  從 `COleLinkingDoc` 衍生您自己的文件類別而不是 `COleDocument`。  
  
2.  建立 OLE 類別 ID \(**CLSID**\) 應用程式中使用類別 ID 產生器隨附 OLE 開發工具。  
  
3.  註冊 OLE 的應用程式。  
  
4.  建立 `COleTemplateServer` 物件做為應用程式類別的成員。  
  
5.  在您的應用程式類別的 `InitInstance` 成員函式，請執行下列步驟:  
  
    -   藉由呼叫物件的 `ConnectTemplate` 成員函式連接至您的文件範本的 `COleTemplateServer` 物件。  
  
    -   呼叫 **COleTemplateServer::RegisterAll** 成員函式來註冊這個 OLE 系統的所有類別物件。  
  
    -   請呼叫 `COleTemplateServer::UpdateRegistry`。  如果應用程式未啟動與「\/Embedded」參數，對 `UpdateRegistry` 的唯一參數應該是 `OAT_CONTAINER` 。  這個註冊應用程式做為可以支援連接至內嵌物件的容器。  
  
         如果應用程式用「\/Embedded」參數啟動，不應該顯示它的主視窗，類似於伺服器應用程式。  
  
 MFC OLE 範例 [OCLIENT](../top/visual-cpp-samples.md) 實作這個功能。  如需有關如何進行的範例，請在這個範例應用程式 OCLIENT.CPP 檔案的 `InitInstance` 函式。  
  
## 請參閱  
 [容器](../mfc/containers.md)   
 [伺服器](../mfc/servers.md)
---
title: "TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "安裝 ODBC"
  - "MFC, 資料庫應用程式"
  - "ODBC, 與 MFC"
  - "ODBC, 安裝"
  - "設定, ODBC 安裝程式"
  - "TN048"
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN048：撰寫 MFC 資料庫應用程式的 ODBC 安裝和管理程式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 使用 MFC 資料庫類別的應用程式需要安裝 ODBC 元件的安裝程式。  它們可能也需要將擷取關於可用驅動程式的資訊，指定預設磁碟機和設定資料來源的 ODBC 管理員程式。  這個會描述使用 ODBC 安裝程式 API 撰寫這些程式。  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> 寫入 ODBC 安裝程式  
 MFC 資料庫應用程式要求 ODBC 驅動程式管理員 \(ODBC.DLL\) 和 ODBC 驅動程式可以有資料來源。  許多 ODBC 驅動程式可能需要其他網路通訊和 DLL。  大部分的 ODBC 驅動程式隨附於安裝必要的 ODBC 元件的安裝程式。  使用 MFC 資料庫類別的應用程式開發人員可以:  
  
-   根據安裝的元件 ODBC 驅動程式特定安裝程式。  這不需要在部分的開發人員的進一步工作可以轉散發驅動程式的安裝程式。  
  
-   或者，您可以撰寫自己的安裝程式，安裝驅動程式管理員和驅動程式。  
  
 ODBC 安裝程式 API 可用來寫入應用程式特定的安裝程式。  在安裝程式 API 的函式是由 ODBC 安裝程式 DLL \(在 16 位元 Windows 上為在 Win32 中 ODBCINST.DLL 和 ODBCCP32.DLL 實作。  應用程式可以呼叫安裝程式 DLL 的 **SQLInstallODBC** ，將安裝 ODBC 驅動程式管理員、ODBC 驅動程式和所有必要的轉換。  然後記錄安裝的驅動程式和轉譯 ODBCINST.INI 檔案 \(或註冊的，在 NT\)。  **SQLInstallODBC** 要求完整路徑 ODBC.INF 檔案，其中包含要安裝的驅動程式的清單和描述檔包含每個驅動程式。  它也包含驅動程式管理員和轉譯的類似資訊。  驅動程式開發人員通常會提供 ODBC.INF 檔案。  
  
 程式可能也會安裝個別的 ODBC 元件。  安裝驅動程式管理員，在安裝程式 DLL 的程式第一次呼叫 **SQLInstallDriverManager** 取得驅動程式管理員的目標目錄。  這通常是 Windows DLL 所在的目錄。  在程式 ODBC.INF 檔案的 \[ODBC 驅動程式管理員\] 部分然後使用資訊複製驅動程式管理員和相關檔案從安裝光碟子目錄。  安裝個別的驅動程式，在安裝程式 DLL 的程式第一次呼叫 **SQLInstallDriver** 加入驅動程式規格到 ODBCINST.INI 檔案 \(或登錄，在 NT\)。  傳回**SQLInstallDriver** 驅動程式的目標目錄— Windows DLL 通常位於的目錄。  在程式 ODBC.INF 檔案的驅動程式的部分然後使用資訊複製驅動程式 DLL 和相關檔案從安裝光碟子目錄。  
  
 如需 ODBC.INF 的詳細資訊， ODBCINST.INI 和使用安裝程式 API，請參閱《ODBC SDK *程式設計人員參考》，* 第 19 章，安裝 ODBC 軟體。  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> 寫入 ODBC 管理員  
 MFC 資料庫應用程式有兩種可能和設定 ODBC 資料來源，如下所示:  
  
-   使用 ODBC 管理員 \(可做為程式或做為主控台項目\)。  
  
-   建立您的程式設定資料來源。  
  
 設定資料來源的程式呼叫函式呼叫安裝程式 DLL。  安裝程式 DLL 呼叫設定 DLL 設定資料來源。  在每一個驅動程式的已設定的 DLL;它可能是驅動程式 DLL 或個別的 DLL。  設定 DLL 提示使用者對於驅動程式需要連接至資料來源和預設轉譯器的，否則，支援的資訊。  然後它會呼叫安裝程式 DLL 和 Windows API 記錄在 ODBC.INI 檔案 \(或登錄\) 這項資訊。  
  
 顯示使用者可以加入的對話方塊，修改和刪除資料來源，安裝程式 DLL 的程式呼叫 **SQLManageDataSources** 。  當安裝程式 DLL 從主控台時，呼叫這個函式叫用。  若要加入、修改，或刪除資料來源， **SQLManageDataSources** 會在設定 DLL 的 **ConfigDSN** 驅動程式的與該資料來源。  直接加入、修改，或刪除資料來源，程式會在安裝程式 DLL 的 **SQLConfigDataSource** 。  程式會藉由指定動作會以資料來源和選項的名稱。  **SQLConfigDataSource** 會在設定 DLL 和傳遞的 **ConfigDSN** 它從 **SQLConfigDataSource**的引數。  
  
 如需詳細資訊，請參閱《ODBC SDK 程式設計人員參考 *、* 第 23 章，被設定的 DLL 函式參考和 Chapter 24，安裝程式 DLL 函式參考。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)
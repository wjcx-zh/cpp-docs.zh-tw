---
title: "WinInet 基本概念 | Microsoft Docs"
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
  - "OnStatusCallback 方法"
  - "WinInet 類別, 關於 WinInet 類別"
  - "WinInet 類別, 顯示進度"
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# WinInet 基本概念
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 WinInet 加入支援 FTP 從您的應用程式中下載及上載檔案。  當您搜尋和下載檔案時，您可以覆寫 [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) 並使用 `dwContext` 參數提供進度資訊給使用者。  
  
 本文章包含下列主題：  
  
-   [建立非常簡單的瀏覽器](#_core_create_a_very_simple_browser)  
  
-   [下載 Web 網頁](#_core_download_a_web_page)  
  
-   [FTP 檔案](#_core_ftp_a_file)  
  
-   [擷取 Gopher 目錄](#_core_retrieve_a_gopher_directory)  
  
-   [在傳送檔案時，會顯示進度資訊](#_core_display_progress_information_while_transferring_files)  
  
 下列程式碼摘要將示範如何建立簡單的瀏覽器、下載網頁、FTP 檔案和搜尋 Gopher 檔案。  它們並不是完整的範例且並未全部都包含例外狀況處理。  
  
 如需 WinInet 的詳細資訊，請參閱 [Win32 Internet Extension \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)。  
  
##  <a name="_core_create_a_very_simple_browser"></a> 建立非常簡單的瀏覽器  
 [!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/CPP/wininet-basics_1.cpp)]  
  
##  <a name="_core_download_a_web_page"></a> 下載 Web 網頁  
 [!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/CPP/wininet-basics_2.cpp)]  
  
##  <a name="_core_ftp_a_file"></a> FTP 檔案  
 [!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/CPP/wininet-basics_3.cpp)]  
  
##  <a name="_core_retrieve_a_gopher_directory"></a> 擷取 Gopher 目錄  
 [!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/CPP/wininet-basics_4.cpp)]  
  
## 使用 OnStatusCallback  
 當使用 WinInet 分類時，您可以使用應用程式的 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件的 [OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) 成員擷取狀態資訊。  如果您衍生您自己的 `CInternetSession` 物件，此物件覆寫 `OnStatusCallback`，並啟用狀態回呼， MFC 在那個網際網路工作階段中將呼叫將進度資訊的 `OnStatusCallback` 函式有關所有活動。  
  
 由於單一工作階段可能支援多個連結 \(在其存留期可能會執行許多不同的作業\)，`OnStatusCallback` 需要一個機制來辨識與特定連接或交易得每個狀態變更。  機制是由提供給許多在 WinInet 支援的成員函式的內容 ID 參數來提供。  這個參數型別一定是 `DWORD` 且一定命名為 `dwContext`。  
  
 指定給特定網際網路物件的內容只用來識別物件在 `CInternetSession` 物件的 `OnStatusCallback` 成員中造成的活動。  對 `OnStatusCallback` 的呼叫接收多個參數；這些參數會告知您的應用程式交易和連接取得了什麼進度。  
  
 當您建立 `CInternetSession` 物件時，您可以指定 `dwContext` 參數給建構函式。  `CInternetSession` 不使用內容 ID；相反地，它會傳遞內容 ID 加入至任何 **InternetConnection**\-沒有明確地取得自己的內容 ID 的衍生物件。  然後，他們所建立的 `CInternetConnection` 物件將會傳遞內容 ID 為 `CInternetFile` 物件，如果沒有明確指定不同的內容 ID。  如果，另一方面，您要指定特定內容 ID，物件及它的所有工作都會與該內容 ID 相關聯。  您可以使用內容 ID 識別哪些狀態資訊在 `OnStatusCallback` 函式提供給您。  
  
##  <a name="_core_display_progress_information_while_transferring_files"></a> 在傳送檔案時顯示進度資訊  
 例如，如果您要寫一個建立連接與 FTP 伺服器讀取檔案並連接至 HTTP 伺服器取得 Web 網頁的應用程式，您會有 `CInternetSession` 物件、兩個 `CInternetConnection` 物件 \(一個是 **CFtpSession** ，另一個是 **CHttpSession**\) 和兩個 `CInternetFile` 物件 \(每個連接會有一個\)。  如果您為 `dwContext` 參數使用預設值，您將無法區別表示 FTP 連接進度的引動過程和表示 HTTP 連接進度的 `OnStatusCallback` 引動過程之間的差別。  如果您指定 `dwContext` ID \(您可以在 `OnStatusCallback`之後測試\)，您就知道哪個作業產生回呼。  
  
## 請參閱  
 [MFC 網際網路程式設計基本概念](../mfc/mfc-internet-programming-basics.md)   
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)
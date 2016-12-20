---
title: "網際網路用戶端類別的必要條件 | Microsoft Docs"
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
  - "類別 [C++], 連接"
  - "連接 [C++], 的類別"
  - "檔案 [C++], 讀取"
  - "檔案 [C++], 寫入至"
  - "FTP (檔案傳輸通訊協定), MFC 類別"
  - "Gopher 用戶端應用程式"
  - "Gopher 必要條件"
  - "HTTP, 網際網路用戶端的必要條件"
  - "網際網路 [C++], 連接"
  - "網際網路用戶端類別必要條件 [C++]"
  - "網際網路檔案 [C++], 寫入至"
  - "必要條件, 網際網路用戶端類別"
  - "URL [C++], 網際網路用戶端應用程式"
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 網際網路用戶端類別的必要條件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

網際網路用戶端採取的特定動作 \(例如讀取檔案\)，有必要動作 \(在此情況中，建立網際網路連線\)。  下表列出必要條件一些用戶端執行動作。  
  
### 一般網際網路、URL \(FTP、HTTP 或 Gopher\)  
  
|動作|必要條件|  
|--------|----------|  
|建立連接。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 建立網際網路用戶端應用程式的基礎。|  
|開啟 URL。|建立連接。  呼叫 [CInternetSession::OpenURL](../Topic/CInternetSession::OpenURL.md)。  `OpenURL` 函式會傳回唯讀資源物件。|  
|讀取 URL 資料。|開啟 URL。  呼叫 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|設定網際網路選項。|建立連接。  呼叫 [CInternetSession::SetOption](../Topic/CInternetSession::SetOption.md)。|  
|設定要呼叫的函式與狀態資訊。|建立連接。  呼叫 [CInternetSession::EnableStatusCallback](../Topic/CInternetSession::EnableStatusCallback.md)。  覆寫處理呼叫的 [CInternetSession::OnStatusCallback](../Topic/CInternetSession::OnStatusCallback.md) 。|  
  
### FTP  
  
|動作|必要條件|  
|--------|----------|  
|建立 FTP 連接。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 為網際網路用戶端應用程式的基礎。  呼叫建立 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 物件的 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md) 。|  
|尋找第一個資源。|建立 FTP 連接。  建立 [CFtpFileFind](../mfc/reference/cftpfilefind-class.md) 物件。  呼叫 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|  
|列舉所有可用的資源。|尋找第一個檔案。  呼叫 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md) ，直到傳回 false。|  
|開啟 FTP 檔案。|建立 FTP 連接。  呼叫 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md) 來建立和開啟 [CInternetFile](../mfc/reference/cinternetfile-class.md) 物件。|  
|讀取 FTP 檔案。|開啟具有讀取權限的 FTP 檔案。  呼叫 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|寫入 FTP 檔案。|開啟具有寫入權限的 FTP 檔案。  呼叫 [CInternetFile::Write](../Topic/CInternetFile::Write.md)。|  
|變更伺服器上的用戶端的目錄。|建立 FTP 連接。  呼叫 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|  
|擷取伺服器的用戶端的目前目錄。|建立 FTP 連接。  呼叫 [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md)。|  
  
### HTTP  
  
|動作|必要條件|  
|--------|----------|  
|建立 HTTP 連接。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 為網際網路用戶端應用程式的基礎。  呼叫建立 [CHttpConnection](../mfc/reference/chttpconnection-class.md) 物件的 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md) 。|  
|開啟的檔案。|建立 HTTP 連接。  呼叫建立 [CHttpFile](../mfc/reference/chttpfile-class.md) 物件的 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md) 。  呼叫 [CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md)。  呼叫 [CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)。|  
|讀取的檔案。|開啟的檔案。  呼叫 [CInternetFile::Read](../Topic/CInternetFile::Read.md)。|  
|取得與 HTTP 要求的相關資訊。|建立 HTTP 連接。  呼叫建立 [CHttpFile](../mfc/reference/chttpfile-class.md) 物件的 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md) 。  呼叫 [CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md)。|  
  
### Gopher  
  
|動作|必要條件|  
|--------|----------|  
|建立 Gopher 連接。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 為網際網路用戶端應用程式的基礎。  呼叫 [CGopherConnection](../mfc/reference/cgopherconnection-class.md)的 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md) 。|  
|尋找在目前目錄中的第一個檔案。|建立 Gopher 連接。  建立 [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md) 物件。  呼叫建立 [CGopherLocator](../mfc/reference/cgopherlocator-class.md) 物件的 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md) 。  透過定位器對 [CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)。  如果您稍後需要它，請呼叫 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md) 取得檔案的定位器。|  
|列舉所有可用的檔案。|尋找第一個檔案。  呼叫 [CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md) ，直到傳回 false。|  
|開啟 Gopher 檔案。|建立 Gopher 連接。  建立使用 [CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md) 產生 Gopher 定位器或尋找具有 [CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)的定位器。  呼叫 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)。|  
|讀取 Gopher 檔案。|開啟 Gopher 檔案。  使用 [CGopherFile](../mfc/reference/cgopherfile-class.md)。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [建立網際網路用戶端應用程式的 MFC 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
---
title: 網際網路用戶端類別必要條件 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6c16c3658ee5d27def4892997c50115dc0b8831
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="prerequisites-for-internet-client-classes"></a>網際網路用戶端類別的必要條件
有些網際網路用戶端 （例如讀取檔案） 所採取的動作 （在此情況下，建立網際網路連線） 中有一些必要的動作。 下表列出一些用戶端動作的必要條件。  
  
### <a name="general-internet-url-ftp-gopher-or-http"></a>一般網際網路 URL （FTP、 Gopher 或 HTTP）  
  
|動作|必要條件|  
|------------|------------------|  
|建立連線。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)建立網際網路用戶端應用程式的基礎。|  
|開啟的 URL。|建立連線。 呼叫[cinternetsession:: Openurl](../mfc/reference/cinternetsession-class.md#openurl)。 `OpenURL`函式會傳回唯讀資源物件。|  
|URL 讀取資料。|開啟的 URL。 呼叫[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|  
|設定網際網路選項。|建立連線。 呼叫[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)。|  
|設定與狀態資訊要呼叫的函式。|建立連線。 呼叫[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)。 覆寫[CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)以處理呼叫。|  
  
### <a name="ftp"></a>FTP  
  
|動作|必要條件|  
|------------|------------------|  
|建立 FTP 連接。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)作為此網際網路用戶端應用程式的基礎。 呼叫[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)建立[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。|  
|尋找第一個資源。|建立 FTP 連接。 建立[CFtpFileFind](../mfc/reference/cftpfilefind-class.md)物件。 呼叫[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|  
|列舉所有可用的資源。|尋找第一個檔案。 呼叫[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)直到它傳回 FALSE。|  
|開啟 FTP 檔案。|建立 FTP 連接。 呼叫[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)以建立並開啟[CInternetFile](../mfc/reference/cinternetfile-class.md)物件。|  
|讀取 FTP 檔案。|開啟 FTP 檔案具有讀取存取權。 呼叫[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|  
|寫入 FTP 檔案。|開啟 FTP 檔案具有寫入存取權。 呼叫[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)。|  
|變更伺服器上的用戶端目錄。|建立 FTP 連接。 呼叫[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|  
|擷取用戶端的伺服器上目前的目錄。|建立 FTP 連接。 呼叫[cftpconnection:: Getcurrentdirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)。|  
  
### <a name="http"></a>HTTP  
  
|動作|必要條件|  
|------------|------------------|  
|建立 HTTP 連線。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)作為此網際網路用戶端應用程式的基礎。 呼叫[CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)建立[CHttpConnection](../mfc/reference/chttpconnection-class.md)物件。|  
|開啟 HTTP 檔案。|建立 HTTP 連線。 呼叫[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)建立[Cinternetfile](../mfc/reference/chttpfile-class.md)物件。 呼叫[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)。 呼叫[CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest)。|  
|讀取 HTTP 檔案。|開啟 HTTP 檔案。 呼叫[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)。|  
|取得 HTTP 要求的相關資訊。|建立 HTTP 連線。 呼叫[chttpconnection::](../mfc/reference/chttpconnection-class.md#openrequest)建立[Cinternetfile](../mfc/reference/chttpfile-class.md)物件。 呼叫[CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo)。|  
  
### <a name="gopher"></a>gopher  
  
|動作|必要條件|  
|------------|------------------|  
|建立 gopher 連線。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)作為此網際網路用戶端應用程式的基礎。 呼叫[CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)建立[CGopherConnection](../mfc/reference/cgopherconnection-class.md)。|  
|目前目錄中尋找第一個檔案。|建立 gopher 連線。 建立[CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)物件。 呼叫[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)建立[CGopherLocator](../mfc/reference/cgopherlocator-class.md)物件。 傳遞到定位器[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)。 呼叫[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)取得檔案的定位器，如果您日後需要。|  
|列舉所有可用的檔案。|尋找第一個檔案。 呼叫[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)直到它傳回 FALSE。|  
|開啟 gopher 檔案。|建立 gopher 連線。 建立與 gopher 定位器[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)或找不到與定位器[CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)。 呼叫[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)。|  
|讀取 gopher 檔案。|開啟 gopher 檔案。 使用[CGopherFile](../mfc/reference/cgopherfile-class.md)。|  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [建立網際網路用戶端應用程式的 MFC 類別](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)

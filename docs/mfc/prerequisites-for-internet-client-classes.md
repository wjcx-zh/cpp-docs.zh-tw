---
title: 網際網路用戶端類別的必要條件
ms.date: 11/04/2016
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
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619837"
---
# <a name="prerequisites-for-internet-client-classes"></a>網際網路用戶端類別的必要條件

網際網路用戶端（例如，讀取檔案）所採取的一些動作，會有必要的動作（在此案例中為建立網際網路連線）。 下表列出某些用戶端動作的必要條件。

### <a name="general-internet-url-ftp-gopher-or-http"></a>一般網際網路 URL （FTP、Gopher 或 HTTP）

|動作|必要條件|
|------------|------------------|
|建立連線。|建立[CInternetSession](reference/cinternetsession-class.md)以建立網際網路用戶端應用程式的基礎。|
|開啟 URL。|建立連線。 呼叫[CInternetSession：： OpenURL](reference/cinternetsession-class.md#openurl)。 函式會傳回 `OpenURL` 唯讀的資源物件。|
|讀取 URL 資料。|開啟 URL。 呼叫[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|設定網際網路選項。|建立連線。 呼叫[CInternetSession：： SetOption](reference/cinternetsession-class.md#setoption)。|
|設定要以狀態資訊呼叫的函式。|建立連線。 呼叫[CInternetSession：： EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback)。 覆寫[CInternetSession：： OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback)以處理呼叫。|

### <a name="ftp"></a>FTP

|動作|必要條件|
|------------|------------------|
|建立 FTP 連接。|建立[CInternetSession](reference/cinternetsession-class.md)做為此網際網路用戶端應用程式的基礎。 呼叫[CInternetSession：： GetFtpConnection](reference/cinternetsession-class.md#getftpconnection)以建立[CFtpConnection](reference/cftpconnection-class.md)物件。|
|尋找第一個資源。|建立 FTP 連接。 建立[CFtpFileFind](reference/cftpfilefind-class.md)物件。 呼叫[CFtpFileFind：： FindFile](reference/cftpfilefind-class.md#findfile)。|
|列舉所有可用的資源。|尋找第一個檔案。 呼叫[CFtpFileFind：： FindNextFile](reference/cftpfilefind-class.md#findnextfile) ，直到它傳回 FALSE。|
|開啟 FTP 檔案。|建立 FTP 連接。 呼叫[CFtpConnection：： OpenFile](reference/cftpconnection-class.md#openfile)以建立並開啟[CInternetFile](reference/cinternetfile-class.md)物件。|
|讀取 FTP 檔案。|開啟具有讀取權限的 FTP 檔案。 呼叫[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|寫入 FTP 檔案。|開啟具有寫入權限的 FTP 檔案。 呼叫[CInternetFile：： Write](reference/cinternetfile-class.md#write)。|
|變更伺服器上的用戶端目錄。|建立 FTP 連接。 呼叫[CFtpConnection：： SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory)。|
|抓取用戶端在伺服器上的目前的目錄。|建立 FTP 連接。 呼叫[CFtpConnection：： GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory)。|

### <a name="http"></a>HTTP

|動作|必要條件|
|------------|------------------|
|建立 HTTP 連接。|建立[CInternetSession](reference/cinternetsession-class.md)做為此網際網路用戶端應用程式的基礎。 呼叫[CInternetSession：： GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection)以建立[CHttpConnection](reference/chttpconnection-class.md)物件。|
|開啟 HTTP 檔案。|建立 HTTP 連接。 呼叫[CHttpConnection：： OpenRequest](reference/chttpconnection-class.md#openrequest)以建立[CHttpFile](reference/chttpfile-class.md)物件。 呼叫[CHttpFile：： AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders)。 呼叫[CHttpFile：： SendRequest](reference/chttpfile-class.md#sendrequest)。|
|讀取 HTTP 檔案。|開啟 HTTP 檔案。 呼叫[CInternetFile：： Read](reference/cinternetfile-class.md#read)。|
|取得 HTTP 要求的相關資訊。|建立 HTTP 連接。 呼叫[CHttpConnection：： OpenRequest](reference/chttpconnection-class.md#openrequest)以建立[CHttpFile](reference/chttpfile-class.md)物件。 呼叫[CHttpFile：： QueryInfo](reference/chttpfile-class.md#queryinfo)。|

### <a name="gopher"></a>Gopher

|動作|必要條件|
|------------|------------------|
|建立 gopher 連接。|建立[CInternetSession](reference/cinternetsession-class.md)做為此網際網路用戶端應用程式的基礎。 呼叫[CInternetSession：： GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection)來建立[CGopherConnection](reference/cgopherconnection-class.md)。|
|尋找目前目錄中的第一個檔案。|建立 gopher 連接。 建立[CGopherFileFind](reference/cgopherfilefind-class.md)物件。 呼叫[CGopherConnection：： CreateLocator](reference/cgopherconnection-class.md#createlocator)以建立[CGopherLocator](reference/cgopherlocator-class.md)物件。 將定位器傳遞至[CGopherFileFind：： FindFile](reference/cgopherfilefind-class.md#findfile)。 如果您稍後需要，請呼叫[CGopherFileFind：： GetLocator](reference/cgopherfilefind-class.md#getlocator)來取得檔案的定位器。|
|列舉所有可用的檔案。|尋找第一個檔案。 呼叫[CGopherFileFind：： FindNextFile](reference/cgopherfilefind-class.md#findnextfile) ，直到它傳回 FALSE。|
|開啟 gopher 檔案。|建立 gopher 連接。 使用[CGopherConnection：： CreateLocator](reference/cgopherconnection-class.md#createlocator)建立 gopher 定位器，或尋找具有[CGopherFileFind：： GetLocator](reference/cgopherfilefind-class.md#getlocator)的定位器。 呼叫[CGopherConnection：： OpenFile](reference/cgopherconnection-class.md#openfile)。|
|讀取 gopher 檔案。|開啟 gopher 檔案。 使用[CGopherFile](reference/cgopherfile-class.md)。|

## <a name="see-also"></a>另請參閱

[Win32 網際網路擴充功能 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[建立網際網路用戶端應用程式的 MFC 類別](mfc-classes-for-creating-internet-client-applications.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](writing-an-internet-client-application-using-mfc-wininet-classes.md)

---
title: 一般 FTP 用戶端應用程式中的步驟
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: d08edf704e748767f3b566252ad328baf40b55ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307012"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>一般 FTP 用戶端應用程式中的步驟

一般 FTP 用戶端應用程式會建立[CInternetSession](../mfc/reference/cinternetsession-class.md)並[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。 請注意，這些 MFC WinInet 類別實際上並控制 proxy 型別設定;IIS 負責。

下表顯示的步驟，您可能會在一般 FTP 用戶端應用程式中執行。

|您的目標|採取的動作|效果|
|---------------|----------------------|-------------|
|開始 FTP 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|
|連線至 FTP 伺服器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|傳回[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。|
|變更到伺服器的新 FTP 目錄。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|變更您在伺服器上目前所連接的目錄。|
|尋找 FTP 目錄中的第一個檔案。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|
|尋找 FTP 目錄中的下一個檔案。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|
|開啟所找到的檔案`FindFile`或`FindNextFile`進行讀取或寫入。|使用[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)，使用檔案名稱由[FindFile](../mfc/reference/cftpfilefind-class.md#findfile)或是[FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|開啟伺服器上的檔案，以便讀取或寫入。 傳回[CInternetFile](../mfc/reference/cinternetfile-class.md)物件。|
|讀取或寫入檔案。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)或是[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)。|讀取或寫入指定的位元組，使用您所提供的緩衝區數目。|
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|
|結束 FTP 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|

## <a name="see-also"></a>另請參閱

[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)

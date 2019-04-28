---
title: 在一般 FTP 用戶端應用程式中刪除檔案的步驟
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 6d2a920d3053a920638dd20a23e1c2334745bbc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307051"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>在一般 FTP 用戶端應用程式中刪除檔案的步驟

下表顯示您可在刪除檔案之典型 FTP 用戶端應用程式中執行的步驟。

|您的目標|採取的動作|效果|
|---------------|----------------------|-------------|
|開始 FTP 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|
|連線至 FTP 伺服器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|傳回[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。|
|請確認您是在 FTP 伺服器的正確目錄。|使用[cftpconnection:: Getcurrentdirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)或是[cftpconnection:: Getcurrentdirectoryasurl](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl)。|根據選取的成員函式，傳回目前在伺服器上連接的目錄名稱或 URL。|
|變更到伺服器的新 FTP 目錄。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|變更您在伺服器上目前所連接的目錄。|
|尋找 FTP 目錄中的第一個檔案。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|
|尋找 FTP 目錄中的下一個檔案。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|
|刪除所找到的檔案`FindFile`或`FindNextFile`。|使用[Findfile](../mfc/reference/cftpconnection-class.md#remove)，使用檔案名稱由`FindFile`或`FindNextFile`。|刪除伺服器上供讀取或寫入的檔案。|
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|
|結束 FTP 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|

## <a name="see-also"></a>另請參閱

[Win32 網際網路延伸模組 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)

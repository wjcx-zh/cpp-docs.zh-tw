---
title: 若要刪除檔案的一般 FTP 用戶端應用程式中的步驟 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1db3418aa96fa779ac3341e12d90d66ba657c4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384529"
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

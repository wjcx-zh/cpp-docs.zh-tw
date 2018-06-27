---
title: 若要刪除檔案的一般 FTP 用戶端應用程式中的步驟 |Microsoft 文件
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
ms.openlocfilehash: 220d1d38c6be33652a8613c60c4e4baa053a8296
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951916"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>在一般 FTP 用戶端應用程式中刪除檔案的步驟
下表顯示您可在刪除檔案之典型 FTP 用戶端應用程式中執行的步驟。  
  
|您的目標|採取的動作|效果|  
|---------------|----------------------|-------------|  
|開始 FTP 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|  
|連線至 FTP 伺服器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|傳回[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。|  
|請確認您是在 FTP 伺服器的正確目錄。|使用[cftpconnection:: Getcurrentdirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)或[cftpconnection:: Getcurrentdirectoryasurl](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl)。|根據選取的成員函式，傳回目前在伺服器上連接的目錄名稱或 URL。|  
|變更到伺服器的新 FTP 目錄。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|變更您在伺服器上目前所連接的目錄。|  
|尋找 FTP 目錄中的第一個檔案。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|  
|尋找 FTP 目錄中的下一個檔案。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|  
|刪除檔案找到`FindFile`或`FindNextFile`。|使用[CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove)，所使用的檔案名稱傳回`FindFile`或`FindNextFile`。|刪除伺服器上供讀取或寫入的檔案。|  
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|  
|結束 FTP 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)

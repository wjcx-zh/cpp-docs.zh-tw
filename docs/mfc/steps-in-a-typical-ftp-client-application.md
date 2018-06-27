---
title: 一般 FTP 用戶端應用程式中的步驟 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fe5a55afda9e77db6e8baddd68c09f4250071bb
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951197"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>一般 FTP 用戶端應用程式中的步驟
一般 FTP 用戶端應用程式建立[CInternetSession](../mfc/reference/cinternetsession-class.md)和[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。 請注意，這些 MFC WinInet 類別實際上並控制 proxy 型別設定;IIS 會執行。  
  
 另請參閱下列知識庫文章：  
  
-   如何： FTP 與 CERN 為基礎的 Proxy 使用 WinInet 應用程式開發介面 (發行項識別碼： Q166961)  
  
-   範例： FTP CERN 密碼與受保護的 Proxy (發行項識別碼： Q216214)  
  
-   網際網路服務管理員無法顯示已安裝的 Proxy 服務 (發行項識別碼： Q216802)  
  
 下表顯示的步驟，您可能會在一般 FTP 用戶端應用程式中執行。  
  
|您的目標|採取的動作|效果|  
|---------------|----------------------|-------------|  
|開始 FTP 工作階段。|建立[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|初始化 WinInet 並連接至伺服器。|  
|連線至 FTP 伺服器。|使用[cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)。|傳回[CFtpConnection](../mfc/reference/cftpconnection-class.md)物件。|  
|變更到伺服器的新 FTP 目錄。|使用[cftpconnection:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)。|變更您在伺服器上目前所連接的目錄。|  
|尋找 FTP 目錄中的第一個檔案。|使用[cftpfilefind:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)。|尋找第一個檔案。 如果找不到檔案則傳回 FALSE。|  
|尋找 FTP 目錄中的下一個檔案。|使用[cftpfilefind:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|尋找下一個檔案。 如果找不到檔案則傳回 FALSE。|  
|開啟檔案所找到`FindFile`或`FindNextFile`進行讀取或寫入。|使用[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)，所使用的檔案名稱傳回[FindFile](../mfc/reference/cftpfilefind-class.md#findfile)或[FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)。|開啟伺服器上的檔案進行讀取或寫入。 傳回[CInternetFile](../mfc/reference/cinternetfile-class.md)物件。|  
|讀取或寫入檔案。|使用[cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)或[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)。|讀取或寫入指定的位元組，使用您提供的緩衝區數目。|  
|處理例外狀況。|使用[CInternetException](../mfc/reference/cinternetexception-class.md)類別。|處理所有通用網際網路例外狀況類型。|  
|結束 FTP 工作階段。|處置[CInternetSession](../mfc/reference/cinternetsession-class.md)物件。|自動清除開啟檔案控制代碼和連接。|  
  
## <a name="see-also"></a>另請參閱  
 [Win32 網際網路擴充功能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)

---
title: "在一般 FTP 用戶端應用程式中刪除檔案的步驟 | Microsoft Docs"
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
  - "FTP (檔案傳輸通訊協定), 用戶端應用程式"
  - "網際網路應用程式, FTP 用戶端應用程式"
  - "網際網路用戶端應用程式, FTP 刪除"
  - "WinInet 類別, FTP"
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在一般 FTP 用戶端應用程式中刪除檔案的步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表顯示您在典型 FTP 用戶端應用程式可能會執行刪除檔案的步驟。  
  
|您的目標|您要採取的動作|效果|  
|----------|-------------|--------|  
|啟動 FTP 工作階段。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|初始化 WinInet 並連接到伺服器。|  
|連接到 FTP。|使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。|這個屬性會傳回 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 物件。|  
|請檢查以確定您是在 FTP 伺服器的正確目錄。|使用 [CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md) 或 [CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md)。|根據選取的成員函式傳回您目前連接到目錄伺服器的名稱或 URL。|  
|切換到伺服器上新的FTP目錄。|使用 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|變更您目前連接至伺服器上的目錄。|  
|尋找在 FTP 目錄的第一個檔案。|使用 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|尋找第一個檔案。  如果找不到檔案則回傳 false。|  
|尋找在 FTP 目錄的下一個檔案。|使用 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)。|尋找下一個檔案。  如果找不到檔案，則傳回 FALSE。|  
|刪除 **FindFile** 或 `FindNextFile`找到的檔案。|使用 [CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md)，或使用 **FindFile** `FindNextFile`傳回的檔案名稱。|刪除伺服器上的檔案以讀取或寫入。|  
|處理例外狀況。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 類別。|處理所有通用網際網路例外狀況型別。|  
|結束FTP工作階段。|處理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|自動清除開啟檔案控制代碼和連接。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
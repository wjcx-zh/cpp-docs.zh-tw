---
title: "一般 FTP 用戶端應用程式中的步驟 | Microsoft Docs"
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
  - "FTP (檔案傳輸通訊協定)"
  - "FTP (檔案傳輸通訊協定), 用戶端應用程式"
  - "網際網路應用程式, FTP 用戶端應用程式"
  - "網際網路用戶端應用程式, FTP 表格"
  - "WinInet 類別, FTP"
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般 FTP 用戶端應用程式中的步驟
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

典型的 FTP 用戶端應用程式建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 和 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 物件。  請注意這些 MFC WinInet 類別並未真正控制 Proxy 型別設定;IIS。  
  
 此外，請參閱下列知識庫文件:  
  
-   HOWTO:使用以歐元核子研究委員會的 Proxy 的 FTP 使用 WinInet API \(文章 ID:Q166961\)  
  
-   範例:使用以歐元核子研究委員會的密碼保護的 Proxy \(文章 ID 的 FTP:Q216214\)  
  
-   顯示安裝 Proxy 服務的網際網路服務管理員失敗 \(文章 ID:Q216802\)  
  
 下表顯示您在一般FTP用戶端應用程式可以執行的步驟。  
  
|您的目標|您要採取的動作。|效果|  
|----------|--------------|--------|  
|啟動 FTP 工作階段。|建立 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|初始化 WinInet 並連接到伺服器。|  
|連接到 FTP。|使用 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)。|這個屬性會傳回 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 物件。|  
|切換到伺服器上新的FTP目錄。|使用 [CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)。|變更您目前連接至伺服器上的目錄。|  
|尋找在 FTP 目錄的第一個檔案。|使用 [CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)。|尋找第一個檔案。  如果找不到檔案則回傳 false。|  
|尋找在 FTP 目錄的下一個檔案。|使用 [CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)。|尋找下一個檔案。  如果找不到檔案，則傳回 FALSE。|  
|開啟 **FindFile** 或 `FindNextFile` 找到的檔案讀取或寫入。|使用 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)，使用 [FindFile](../Topic/CFtpFileFind::FindFile.md) 或 [FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)傳回的檔案名稱。|開啟伺服器上的檔案以讀取或寫入。  這個屬性會傳回 [CInternetFile](../mfc/reference/cinternetfile-class.md) 物件。|  
|讀取或寫入檔案。|使用 [CInternetFile::Read](../Topic/CInternetFile::Read.md) 或 [CInternetFile::Write](../Topic/CInternetFile::Write.md)。|使用您提供的緩衝區讀取或寫入指定的位元組數。|  
|處理例外狀況。|使用 [CInternetException](../mfc/reference/cinternetexception-class.md) 類別。|處理所有通用網際網路例外狀況型別。|  
|結束FTP工作階段。|處理 [CInternetSession](../mfc/reference/cinternetsession-class.md) 物件。|自動清除開啟檔案控制代碼和連接。|  
  
## 請參閱  
 [Win32 網際網路擴充功能 \(WinInet\)](../mfc/win32-internet-extensions-wininet.md)   
 [網際網路用戶端類別的必要條件](../mfc/prerequisites-for-internet-client-classes.md)   
 [使用 MFC WinInet 類別建立網際網路用戶端應用程式](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
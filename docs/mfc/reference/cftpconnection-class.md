---
title: "CFtpConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFtpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpConnection class"
  - "FTP (檔案傳輸通訊協定), 建立連接"
  - "Internet connections, FTP"
  - "Internet services, FTP"
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFtpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理與網際網路伺服器的 FTP 連接並允許目錄和檔案的直接操作該伺服器。  
  
## 語法  
  
```  
class CFtpConnection : public CInternetConnection  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFtpConnection::CFtpConnection](../Topic/CFtpConnection::CFtpConnection.md)|建構 `CFtpConnection` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFtpConnection::Command](../Topic/CFtpConnection::Command.md)|命令直接傳送至 FTP 伺服器。|  
|[CFtpConnection::CreateDirectory](../Topic/CFtpConnection::CreateDirectory.md)|在伺服器上建立目錄。|  
|[CFtpConnection::GetCurrentDirectory](../Topic/CFtpConnection::GetCurrentDirectory.md)|取得這個連接的目前目錄。|  
|[CFtpConnection::GetCurrentDirectoryAsURL](../Topic/CFtpConnection::GetCurrentDirectoryAsURL.md)|取得這個連接的目前目錄做為 URL。|  
|[CFtpConnection::GetFile](../Topic/CFtpConnection::GetFile.md)|從連接的伺服器取得檔案|  
|[CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)|開啟連接之伺服器上的檔案。|  
|[CFtpConnection::PutFile](../Topic/CFtpConnection::PutFile.md)|在伺服器上的檔案。|  
|[CFtpConnection::Remove](../Topic/CFtpConnection::Remove.md)|從伺服器刪除檔案。|  
|[CFtpConnection::RemoveDirectory](../Topic/CFtpConnection::RemoveDirectory.md)|從伺服器移除指定的目錄。|  
|[CFtpConnection::Rename](../Topic/CFtpConnection::Rename.md)|提供在伺服器中重新命名檔案。|  
|[CFtpConnection::SetCurrentDirectory](../Topic/CFtpConnection::SetCurrentDirectory.md)|設定目前 FTP 目錄。|  
  
## 備註  
 FTP 是 MFC WinInet 類別可辨認的三項網際網路服務之一。  
  
 使用 FTP 網際網路伺服器要通訊，您必須先建立 [CInternetSession](../../mfc/reference/cinternetsession-class.md)執行個體，然後建立 `CFtpConnection` 物件。  您絕對不會直接建立物件， `CFtpConnection` 相反地，呼叫 [CInternetSession::GetFtpConnection](../Topic/CInternetSession::GetFtpConnection.md)，建立 `CFtpConnection` 物件並傳回指向它。  
  
 若要進一步了解 `CFtpConnection` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  如需通訊與其他兩個支援服務的詳細資訊， HTTP 和 Gopher，請參閱類別 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 和 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)。  
  
## 範例  
 請參閱在 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 類別概觀中的範例。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CFtpConnection`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)
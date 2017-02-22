---
title: "CHttpConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHttpConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpConnection class"
  - "連接至伺服器"
  - "連接至伺服器, HTTP 伺服器"
  - "連接 [C++], HTTP"
  - "HTTP 連接"
  - "HTTP 伺服器, 連接至"
  - "Internet connections, HTTP"
  - "Internet protocols"
  - "Internet protocols, HTTP"
  - "Internet server, HTTP"
  - "協定, HTTP"
  - "伺服器, 連接至"
ms.assetid: a402b662-c445-4988-800d-c8278551babe
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CHttpConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理至 HTTP 伺服器的連接。  
  
## 語法  
  
```  
class CHttpConnection : public CInternetConnection  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHttpConnection::CHttpConnection](../Topic/CHttpConnection::CHttpConnection.md)|建立 `CHttpConnection` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)|開啟 HTTP 要求。|  
  
## 備註  
 HTTP 是 MFC WinInet 類別實作的三個網際網路伺服器通訊協定之一。  
  
 類別 `CHttpConnection` 包含建構函式和 10% 成員函式， [OpenRequest](../Topic/CHttpConnection::OpenRequest.md)，處理與伺服器的連接使用 HTTP 通訊協定。  
  
 使用 HTTP 伺服器要通訊，您必須先建立 [CInternetSession](../../mfc/reference/cinternetsession-class.md)執行個體，然後建立 [CHttpConnection](#_mfc_chttpconnection) 物件。  您絕對不會直接建立物件， `CHttpConnection` 相反地，呼叫 [CInternetSession::GetHttpConnection](../Topic/CInternetSession::GetHttpConnection.md)，建立 `CHttpConnection` 物件並傳回指向它。  
  
 若要進一步了解 `CHttpConnection` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  如需連接到使用其他兩個支援的網際網路通訊協定的伺服器的詳細資訊，請參閱和 Gopher FTP，請參閱類別 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 和 [CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CHttpConnection`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)
---
title: "CInternetConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CInternetConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asynchronous connections"
  - "CInternetConnection class"
  - "Internet connections"
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CInternetConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理與網際網路伺服器的連接。  
  
## 語法  
  
```  
class CInternetConnection : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInternetConnection::CInternetConnection](../Topic/CInternetConnection::CInternetConnection.md)|建構 `CInternetConnection` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CInternetConnection::GetContext](../Topic/CInternetConnection::GetContext.md)|取得這個連接物件的內容 ID。|  
|[CInternetConnection::GetServerName](../Topic/CInternetConnection::GetServerName.md)|取得伺服器的名稱與連接。|  
|[CInternetConnection::GetSession](../Topic/CInternetConnection::GetSession.md)|取得的指標 [CInternetSession](../../mfc/reference/cinternetsession-class.md) 物件相關聯的連接。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CInternetConnection::operator HINTERNET](../Topic/CInternetConnection::operator%20HINTERNET.md)|對網際網路工作階段的控制代碼。|  
  
## 備註  
 它是 MFC 類別的 [CFtpConnection](../../mfc/reference/cftpconnection-class.md)、 [CHttpConnection](../../mfc/reference/chttpconnection-class.md)和 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)基底類別。  這些類別的每一通訊是提供額外的功能與個別 HTTP、FTP 或 Gopher 伺服器。  
  
 直接使用網際網路伺服器要進行通訊，您必須將 [CInternetSession](../../mfc/reference/cinternetsession-class.md)`CInternetConnection` 物件和物件。  
  
 若要進一步了解 WinInet 類別的運作方式，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)
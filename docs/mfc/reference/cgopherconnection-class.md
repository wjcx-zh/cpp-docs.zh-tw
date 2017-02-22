---
title: "CGopherConnection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGopherConnection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherConnection class"
  - "連接至伺服器"
  - "連接至伺服器, gopher servers"
  - "Gopher 通訊協定"
  - "gopher server"
  - "Internet connections, gopher"
  - "Internet server, gopher"
  - "協定, gopher"
  - "伺服器, 連接至"
  - "服務, gopher"
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGopherConnection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理和 Gopher 網際網路伺服器的連接。  
  
> [!NOTE]
>  類別 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成員已被取代，因為它們已經在 Windows XP 平台上不能運作，但是，會繼續在舊版平台運作。  
  
## 語法  
  
```  
class CGopherConnection : public CInternetConnection  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CGopherConnection::CGopherConnection](../Topic/CGopherConnection::CGopherConnection.md)|建構 `CGopherConnection` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CGopherConnection::CreateLocator](../Topic/CGopherConnection::CreateLocator.md)|建立物件 [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 尋找 Gopher 伺服器上的檔案。|  
|[CGopherConnection::GetAttribute](../Topic/CGopherConnection::GetAttribute.md)|如需擷取至物件的屬性資訊。|  
|[CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md)|開啟至檔案。|  
  
## 備註  
 Gopher 服務是 MFC WinInet 類別可辨認的三項網際網路服務之一。  
  
 類別包含 `CGopherConnection` 處理 Gopher 服務的建構函式和三個其他成員函式: [OpenFile](../Topic/CGopherConnection::OpenFile.md)、 [CreateLocator](../Topic/CGopherConnection::CreateLocator.md)和 [GetAttribute](../Topic/CGopherConnection::GetAttribute.md)。  
  
 與 Gopher 網際網路伺服器要通訊，您必須先建立 [CInternetSession](../../mfc/reference/cinternetsession-class.md)執行個體，然後呼叫 [CInternetSession::GetGopherConnection](../Topic/CInternetSession::GetGopherConnection.md)，建立 `CGopherConnection` 物件並傳回指向它。  您絕對不會直接建立 `CGopherConnection` 物件。  
  
 若要進一步了解 `CGopherConnection` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  如需使用其他兩項所支援的網際網路服務的詳細資訊，請 FTP、HTTP 和類別 [CHttpConnection](../../mfc/reference/chttpconnection-class.md)[CFtpConnection](../../mfc/reference/cftpconnection-class.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)  
  
 `CGopherConnection`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFtpConnection Class](../../mfc/reference/cftpconnection-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CInternetSession Class](../../mfc/reference/cinternetsession-class.md)
---
title: "CGopherFile Class | Microsoft Docs"
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
  - "CGopherFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFile 類別"
  - "gopher protocol files"
  - "網際網路, gopher"
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CGopherFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Gopher 伺服器提供功能來尋找和讀取檔案。  
  
> [!NOTE]
>  類別 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成員已被取代，因為它們已經在 Windows XP 平台上不能運作，但是，會繼續在舊版平台運作。  
  
## 語法  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CGopherFile::CGopherFile](../Topic/CGopherFile::CGopherFile.md)|建構 `CGopherFile` 物件。|  
  
## 備註  
 Gopher 服務不允許使用者將資料寫入至檔案，因為這個服務功能主要做為項目清單是讓介面提供此資訊。  `CGopherFile` 成員函式 **寫入**、 `WriteString`和 `Flush` 沒有為 `CGopherFile`中實作。  在呼叫 `CGopherFile` 的這些函式則為，否則傳回 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要進一步了解 `CGopherFile` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherLocator Class](../../mfc/reference/cgopherlocator-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CGopherConnection Class](../../mfc/reference/cgopherconnection-class.md)
---
title: "CHttpFile Class | Microsoft Docs"
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
  - "CHttpFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHttpFile class"
  - "HTTP 檔案"
  - "HTTP requests, requesting and reading files"
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHttpFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 HTTP 伺服器的功能需求和讀取檔案。  
  
## 語法  
  
```  
class CHttpFile : public CInternetFile  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHttpFile::CHttpFile](../Topic/CHttpFile::CHttpFile.md)|建立 `CHttpFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHttpFile::AddRequestHeaders](../Topic/CHttpFile::AddRequestHeaders.md)|將標頭加入至要求傳送至 HTTP 伺服器。|  
|[CHttpFile::EndRequest](../Topic/CHttpFile::EndRequest.md)|結束要求傳送至具有 [SendRequestEx](../Topic/CHttpFile::SendRequestEx.md) 成員函式之 HTTP 伺服器。|  
|[CHttpFile::GetFileURL](../Topic/CHttpFile::GetFileURL.md)|取得指定之檔案的 URL。|  
|[CHttpFile::GetObject](../Topic/CHttpFile::GetObject.md)|取得物件的直接賓語言在要求至 HTTP 伺服器。|  
|[CHttpFile::GetVerb](../Topic/CHttpFile::GetVerb.md)|取得套用至 HTTP 伺服器的要求的動詞命令。|  
|[CHttpFile::QueryInfo](../Topic/CHttpFile::QueryInfo.md)|傳回回應或要求標頭從 HTTP 伺服器。|  
|[CHttpFile::QueryInfoStatusCode](../Topic/CHttpFile::QueryInfoStatusCode.md)|要擷取狀態碼與 HTTP 要求並將其放置在所提供的 `dwStatusCode` 參數。|  
|[CHttpFile::SendRequest](../Topic/CHttpFile::SendRequest.md)|將要求傳送至 HTTP 伺服器。|  
|[CHttpFile::SendRequestEx](../Topic/CHttpFile::SendRequestEx.md)|使用 `CInternetFile`， [寫入](../Topic/CInternetFile::Write.md) 或 [WriteString](../Topic/CInternetFile::WriteString.md) 方法將要求傳送至 HTTP 伺服器。|  
  
## 備註  
 如果網際網路工作階段讀取 HTTP 伺服器的資料，您必須建立 `CHttpFile`執行個體。  
  
 若要進一步了解 `CHttpFile` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CHttpFile`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpConnection Class](../../mfc/reference/chttpconnection-class.md)
---
title: "CFtpFileFind Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFtpFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFtpFileFind class"
  - "檔案搜尋 [C++]"
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CFtpFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在網際網路上的 FTP 伺服器檔案搜尋的協助。  
  
## 語法  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFtpFileFind::CFtpFileFind](../Topic/CFtpFileFind::CFtpFileFind.md)|建構 `CFtpFileFind` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFtpFileFind::FindFile](../Topic/CFtpFileFind::FindFile.md)|尋找在 FTP 伺服器上的檔案。|  
|[CFtpFileFind::FindNextFile](../Topic/CFtpFileFind::FindNextFile.md)|繼續在前一個呼叫的檔案搜尋到 [FindFile](../Topic/CFtpFileFind::FindFile.md)。|  
|[CFtpFileFind::GetFileURL](../Topic/CFtpFileFind::GetFileURL.md)|取得 URL，包括路徑，找到的檔案。|  
  
## 備註  
 `CFtpFileFind` 包括開始搜尋，尋找檔案，並傳回 URL 或其他描述性資訊有關檔案的成員函式。  
  
 用於網際網路和本機檔案設計的其他 MFC 類別中搜尋包含 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 和 [CFileFind](../../mfc/reference/cfilefind-class.md)。  不論伺服器通訊協定或檔案類型 \(本機電腦或遠端伺服器\)，與 `CFtpFileFind`以外，這些類別為用戶端提供一種緊密的機制來尋找特定檔案。  請注意不要搜尋的 MFC 類別在 HTTP 伺服器，因為不支援 HTTP 對於搜尋所需的直接檔案作業。  
  
 如需如何使用 `CFtpFileFind` 和其他 WinInet 類別的詳細資訊，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 範例  
 下列程式碼示範如何列舉在 FTP 伺服器上的目前目錄中的所有檔案。  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/CPP/cftpfilefind-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)
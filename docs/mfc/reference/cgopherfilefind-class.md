---
title: "CGopherFileFind Class | Microsoft Docs"
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
  - "CGopherFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CGopherFileFind class"
  - "檔案搜尋 [C++]"
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CGopherFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在網際網路上 Gopher 伺服器檔案搜尋的協助。  
  
> [!NOTE]
>  類別 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、 `CGopherLocator` 及其成員已被取代，因為它們已經在 Windows XP 平台上不能運作，但是，會繼續在舊版平台運作。  
  
## 語法  
  
```  
class CGopherFileFind : public CFileFind  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CGopherFileFind::CGopherFileFind](../Topic/CGopherFileFind::CGopherFileFind.md)|建構 `CGopherFileFind` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CGopherFileFind::FindFile](../Topic/CGopherFileFind::FindFile.md)|尋找 Gopher 伺服器的檔案。|  
|[CGopherFileFind::FindNextFile](../Topic/CGopherFileFind::FindNextFile.md)|繼續在前一個呼叫的檔案搜尋到 [FindFile](../Topic/CGopherFileFind::FindFile.md)。|  
|[CGopherFileFind::GetCreationTime](../Topic/CGopherFileFind::GetCreationTime.md)|取得指定之檔案的建立時間。|  
|[CGopherFileFind::GetLastAccessTime](../Topic/CGopherFileFind::GetLastAccessTime.md)|取得指定檔案上次存取時間。|  
|[CGopherFileFind::GetLastWriteTime](../Topic/CGopherFileFind::GetLastWriteTime.md)|取得指定檔案上次被寫入的時間。|  
|[CGopherFileFind::GetLength](../Topic/CGopherFileFind::GetLength.md)|從找到的位置取得檔案的長度，以位元組為單位\)。|  
|[CGopherFileFind::GetLocator](../Topic/CGopherFileFind::GetLocator.md)|取得 `CGopherLocator` 物件。|  
|[CGopherFileFind::GetScreenName](../Topic/CGopherFileFind::GetScreenName.md)|取得 Gopher 螢幕的名稱。|  
|[CGopherFileFind::IsDots](../Topic/CGopherFileFind::IsDots.md)|目前目錄和父目錄標記的測試，在逐一查看檔案時。|  
  
## 備註  
 `CGopherFileFind` 包括開始搜尋，尋找檔案，並傳回檔案的 URL 的成員函式。  
  
 用於網際網路和本機檔案設計的其他 MFC 類別中搜尋包含 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 和 [CFileFind](../../mfc/reference/cfilefind-class.md)。  使用 `CGopherFileFind`以外，這些類別提供一個緊密的機制來尋找特定檔案，不論伺服器通訊協定、檔案類型或位置 \(本機電腦或遠端伺服器\)。請注意不要搜尋的 MFC 類別在 HTTP 伺服器，因為不支援 HTTP 查詢所需的直接檔案作業。  
  
> [!NOTE]
>  `CGopherFileFind` 不受支援的基底類別 [CFileFind](../../mfc/reference/cfilefind-class.md)的下列成員函式:  
  
-   [GetRoot](../Topic/CFileFind::GetRoot.md)  
  
-   [GetFileName](../Topic/CFileFind::GetFileName.md)  
  
-   [GetFilePath](../Topic/CFileFind::GetFilePath.md)  
  
-   [GetFileTitle](../Topic/CFileFind::GetFileTitle.md)  
  
-   [GetFileURL](../Topic/CFileFind::GetFileURL.md)  
  
 此外，在中，當搭配 `CGopherFileFind`， `CFileFind` 成員函式 [IsDots](../Topic/CFileFind::IsDots.md) 一定是 **否**。  
  
 如需如何使用 `CGopherFileFind` 和其他 WinInet 類別的詳細資訊，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CGopherFileFind`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CFileFind Class](../../mfc/reference/cfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)
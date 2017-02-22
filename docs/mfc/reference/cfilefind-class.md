---
title: "CFileFind Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileFind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileFind class"
  - "檔案 [C++], 尋找"
  - "Internet files [C++], 尋找"
  - "local files"
  - "local files, 搜尋"
  - "URLs [C++], 搜尋"
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CFileFind Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行本機檔案搜尋並 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)是和的基底類別 \(Base Class\)，實作網際網路檔案搜尋。  
  
## 語法  
  
```  
class CFileFind : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFileFind::CFileFind](../Topic/CFileFind::CFileFind.md)|建構 `CFileFind` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileFind::Close](../Topic/CFileFind::Close.md)|結束搜尋要求。|  
|[CFileFind::FindFile](../Topic/CFileFind::FindFile.md)|在目錄中搜尋指定的檔案名稱。|  
|[CFileFind::FindNextFile](../Topic/CFileFind::FindNextFile.md)|繼續在前一個呼叫的檔案搜尋到 [FindFile](../Topic/CFileFind::FindFile.md)。|  
|[CFileFind::GetCreationTime](../Topic/CFileFind::GetCreationTime.md)|取得檔案的建立時間。|  
|[CFileFind::GetFileName](../Topic/CFileFind::GetFileName.md)|取得名稱，包括副檔名，找到的檔案。|  
|[CFileFind::GetFilePath](../Topic/CFileFind::GetFilePath.md)|從找到的位置取得檔案的完整路徑。|  
|[CFileFind::GetFileTitle](../Topic/CFileFind::GetFileTitle.md)|取得中找到的檔案的標題。  這個標題不包含副檔名。|  
|[CFileFind::GetFileURL](../Topic/CFileFind::GetFileURL.md)|取得 URL，包括檔案路徑，找到的檔案。|  
|[CFileFind::GetLastAccessTime](../Topic/CFileFind::GetLastAccessTime.md)|取得時間、上次存取檔案的。|  
|[CFileFind::GetLastWriteTime](../Topic/CFileFind::GetLastWriteTime.md)|取得上次變更並儲存檔案的時間。|  
|[CFileFind::GetLength](../Topic/CFileFind::GetLength.md)|從找到的位置取得檔案的長度，以位元組為單位\)。|  
|[CFileFind::GetRoot](../Topic/CFileFind::GetRoot.md)|取得中所描述的檔案之根目錄。|  
|[CFileFind::IsArchived](../Topic/CFileFind::IsArchived.md)|判斷中找到的檔案是否已封存。|  
|[CFileFind::IsCompressed](../Topic/CFileFind::IsCompressed.md)|判斷中找到的檔案是否為壓縮。|  
|[CFileFind::IsDirectory](../Topic/CFileFind::IsDirectory.md)|判斷中找到的檔案是否為目錄。|  
|[CFileFind::IsDots](../Topic/CFileFind::IsDots.md)|判斷中找到的檔案名稱是否具有名稱「」。或「。」，表示實際上是目錄。|  
|[CFileFind::IsHidden](../Topic/CFileFind::IsHidden.md)|判斷中找到的檔案是否為隱藏。|  
|[CFileFind::IsNormal](../Topic/CFileFind::IsNormal.md)|判斷中找到的檔案是否為一般 \(換句話說，沒有其他屬性\)。|  
|[CFileFind::IsReadOnly](../Topic/CFileFind::IsReadOnly.md)|判斷中找到的檔案是否為唯讀。|  
|[CFileFind::IsSystem](../Topic/CFileFind::IsSystem.md)|判斷中找到的檔案是系統檔案。|  
|[CFileFind::IsTemporary](../Topic/CFileFind::IsTemporary.md)|判斷中找到的檔案是否為暫時的。|  
|[CFileFind::MatchesMask](../Topic/CFileFind::MatchesMask.md)|表示要尋找的檔案所要的檔案屬性。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CFileFind::CloseContext](../Topic/CFileFind::CloseContext.md)|關閉目前的搜尋控制代碼所指定的檔案。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFileFind::m\_pTM](../Topic/CFileFind::m_pTM.md)|為 `CAtlTransactionManager` 物件的指標。|  
  
## 備註  
 `CFileFind` 包括開始搜尋，尋找檔案，並傳回檔案的標題、名稱或路徑的成員函式。  對於網際網路搜尋，成員函式 [GetFileURL](../Topic/CFileFind::GetFileURL.md) 傳回檔案的 URL。  
  
 `CFileFind` 是特別設計的其他兩個 MFC 類別的基底類別中搜尋特定伺服器類型: `CGopherFileFind` 特別為可使用 Gopher 伺服器和 `CFtpFileFind` 使用 FTP 伺服器使用。  同時，不論伺服器通訊協定、檔案類型或位置，本機電腦或遠端伺服器上，這三個類別為用戶端提供一種緊密的機制來尋找檔案。  
  
 下列程式碼會列舉在目前目錄中的所有檔案，列印每個檔案的名稱:  
  
 [!code-cpp[NVC_MFCFiles#31](../../mfc/codesnippet/CPP/cfilefind-class_1.cpp)]  
  
 為了維持此範例的簡單性，這段程式碼會使用 Standard C\+\+ 程式庫 `cout` 類別。  `cout` 行可以套用至 `CListBox::AddString`的呼叫取代，例如，在程式使用圖形化使用者介面。  
  
 如需如何使用 `CFileFind` 和其他 WinInet 類別的詳細資訊，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind Class](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind Class](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile Class](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile Class](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile Class](../../mfc/reference/chttpfile-class.md)
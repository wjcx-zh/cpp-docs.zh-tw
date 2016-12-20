---
title: "CInternetFile Class | Microsoft Docs"
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
  - "CInternetFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CInternetFile class"
  - "Internet files"
  - "Internet files, CInternetFile class"
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CInternetFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

允許對檔案的存取權限。會使用網際網路通訊協定的遠端系統。  
  
## 語法  
  
```  
  
class CInternetFile : public CStdioFile  
  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CInternetFile::CInternetFile](../Topic/CInternetFile::CInternetFile.md)|建構 `CInternetFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CInternetFile::Abort](../Topic/CInternetFile::Abort.md)|關閉檔案，忽略任何警告和錯誤。|  
|[CInternetFile::Close](../Topic/CInternetFile::Close.md)|結束 `CInternetFile` 並釋放其資源。|  
|[CInternetFile::Flush](../Topic/CInternetFile::Flush.md)|清除寫入緩衝區的內容並確定在記憶體中的資料會寫入至目標電腦中。|  
|[CInternetFile::GetLength](../Topic/CInternetFile::GetLength.md)|傳回檔案的大小。|  
|[CInternetFile::Read](../Topic/CInternetFile::Read.md)|將指定的位元組數目。|  
|[CInternetFile::ReadString](../Topic/CInternetFile::ReadString.md)|讀取字元資料流。|  
|[CInternetFile::Seek](../Topic/CInternetFile::Seek.md)|重新調整位置開啟檔案的指標。|  
|[CInternetFile::SetReadBufferSize](../Topic/CInternetFile::SetReadBufferSize.md)|將資料讀取緩衝區的大小。|  
|[CInternetFile::SetWriteBufferSize](../Topic/CInternetFile::SetWriteBufferSize.md)|設定將資料寫入緩衝區的大小。|  
|[CInternetFile::Write](../Topic/CInternetFile::Write.md)|寫入指定的位元組數目。|  
|[CInternetFile::WriteString](../Topic/CInternetFile::WriteString.md)|以 null 結尾的字串寫入檔案中。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CInternetFile::operator HINTERNET](../Topic/CInternetFile::operator%20HINTERNET.md)|網際網路控制代碼的轉型運算子。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CInternetFile::m\_hFile](../Topic/CInternetFile::m_hFile.md)|對檔案的控制代碼。|  
  
## 備註  
 提供 [CHttpFile](../../mfc/reference/chttpfile-class.md) 提供基底類別，並 [CGopherFile](../../mfc/reference/cgopherfile-class.md) 檔案分類。  您絕對不會直接建立 `CInternetFile` 物件。  相反地，請透過呼叫 [CGopherConnection::OpenFile](../Topic/CGopherConnection::OpenFile.md) 或 [CHttpConnection::OpenRequest](../Topic/CHttpConnection::OpenRequest.md)建立物件的其中一個衍生類別。  您可以藉由呼叫 [CFtpConnection::OpenFile](../Topic/CFtpConnection::OpenFile.md)也會建立 `CInternetFile` 物件。  
  
 `CInternetFile` 成員函式 **開啟**、 `LockRange`、 `UnlockRange`和 `Duplicate` 沒有為 `CInternetFile`中實作。  如果您呼叫在 `CInternetFile` 的這些函式物件，您會取得 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 若要進一步了解 `CInternetFile` 如何與其他 MFC Internet 類別一起使用，請參閱本文 [Office 方案中使用 WinInet 的網際網路](../../mfc/win32-internet-extensions-wininet.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## 需求  
 **Header:** afxinet.h  
  
## 請參閱  
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CInternetConnection Class](../../mfc/reference/cinternetconnection-class.md)
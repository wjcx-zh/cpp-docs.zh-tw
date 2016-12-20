---
title: "CMemFile Class | Microsoft Docs"
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
  - "CMemFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMemFile class"
  - "memory files"
  - "temporary files, memory files"
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMemFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[C 檔案](../../mfc/reference/cfile-class.md)\-支援記憶體檔案的衍生類別。  
  
## 語法  
  
```  
class CMemFile : public CFile  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CMemFile::CMemFile](../Topic/CMemFile::CMemFile.md)|建構記憶體檔案物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMemFile::Attach](../Topic/CMemFile::Attach.md)|將記憶體區塊中 `CMemFile`。|  
|[CMemFile::Detach](../Topic/CMemFile::Detach.md)|中斷連結記憶體區塊是 `CMemFile` 的並傳回指標至中斷連接的記憶體區塊。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CMemFile::Alloc](../Topic/CMemFile::Alloc.md)|修改記憶體配置行為的覆寫。|  
|[CMemFile::Free](../Topic/CMemFile::Free.md)|修改記憶體解除配置行為的覆寫。|  
|[CMemFile::GrowFile](../Topic/CMemFile::GrowFile.md)|修改行為的覆寫，當成長檔案時。|  
|[CMemFile::Memcpy](../Topic/CMemFile::Memcpy.md)|修改記憶體複製行為的覆寫，以讀取和寫入檔案時。|  
|[CMemFile::Realloc](../Topic/CMemFile::Realloc.md)|修改記憶體重新配置行為的覆寫。|  
  
## 備註  
 這些記憶體檔案的行為就像磁碟檔案，但檔案在 RAM 儲存 \(而非從磁碟。  記憶體檔案是用來快速的暫時儲存區或適合傳送未經處理的位元組或還原序列化的物件在個別處理序之間。  
  
 `CMemFile` 物件可以自動配置自己的記憶體或能夠附加至您的記憶體區塊加入至 `CMemFile` 物件藉由呼叫 [連結](../Topic/CMemFile::Attach.md)。  在任何情況下， `nGrowBytes` ，如果不是零，成長的記憶體檔案記憶體中 `nGrowBytes`大小將自動配置。  
  
 記憶體區塊會自動刪除。 `CMemFile` 物件的解構 `CMemFile` 物件是否一開始配置記憶體，否則，您必須負責解除配置您附加至物件的記憶體。  
  
 您可以透過提供的指標存取記憶體區塊，當您呼叫 [中斷連結](../Topic/CMemFile::Detach.md)中斷它與 `CMemFile` 物件時。  
  
 最常見的用途是建立 `CMemFile``CMemFile` 物件並使用其傳遞 [C 檔案](../../mfc/reference/cfile-class.md) 呼叫成員函式。  請注意，建立 `CMemFile` 的自動開啟它:您不會 [CFile::Open](../Topic/CFile::Open.md)，為磁碟檔案只能透過取得。  由於 `CMemFile` 不使用單向磁碟檔案，而不使用資料成員 `CFile::m_hFile` 並沒有意義。  
  
 `CFile` 成員函式 [複製](../Topic/CFile::Duplicate.md)、 [LockRange](../Topic/CFile::LockRange.md)和 [UnlockRange](../Topic/CFile::UnlockRange.md) 沒有為 `CMemFile`中實作。  如果您呼叫在 `CMemFile` 的這些函式物件，您會取得 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 `CMemFile` 使用執行階段程式庫函式 [malloc](../../c-runtime-library/reference/malloc.md)、 [realloc](../../c-runtime-library/reference/realloc.md)和 [可用](../../c-runtime-library/reference/free.md) 配置，重新配置和解除配置記憶體，而內部封鎖記憶體複本的 [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) ，在讀取和寫入時。  如果要變更這個行為或行為，當 `CMemFile` 成長檔案時，從 `CMemFile` 衍生您的類別並覆寫適當的函式。  
  
 如需 `CMemFile`的相關資訊，請參閱 Microsoft 知識庫文件 [MFC 中的檔案](../../mfc/files-in-mfc.md) 和 [記憶體管理 \(MFC\)](../../mfc/memory-management.md) 並參閱《執行階段 *程式庫參考》的*[檔案處理](../../c-runtime-library/file-handling.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)
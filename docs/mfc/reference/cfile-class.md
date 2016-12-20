---
title: "CFile Class | Microsoft Docs"
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
  - "CFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive class, using with CFile"
  - "CFile class"
  - "檔案 [C++], classes for"
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
caps.latest.revision: 22
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft Foundation Class 檔案的基底類別。  
  
## 語法  
  
```  
class CFile : public CObject  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CFile::CFile](../Topic/CFile::CFile.md)|從路徑或檔案控制代碼的 `CFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CFile::Abort](../Topic/CFile::Abort.md)|關閉忽略任何警告和錯誤的檔案。|  
|[CFile::Close](../Topic/CFile::Close.md)|關閉檔案並刪除物件。|  
|[CFile::Duplicate](../Topic/CFile::Duplicate.md)|會建構以這個檔案的複製物件。|  
|[CFile::Flush](../Topic/CFile::Flush.md)|清除要寫入的所有資料。|  
|[CFile::GetFileName](../Topic/CFile::GetFileName.md)|擷取所選取之檔案的檔名。|  
|[CFile::GetFilePath](../Topic/CFile::GetFilePath.md)|擷取所選取檔案的完整檔案路徑。|  
|[CFile::GetFileTitle](../Topic/CFile::GetFileTitle.md)|擷取所選取檔案的標題。|  
|[CFile::GetLength](../Topic/CFile::GetLength.md)|擷取檔案的長度。|  
|[CFile::GetPosition](../Topic/CFile::GetPosition.md)|擷取目前資料指標。|  
|[CFile::GetStatus](../Topic/CFile::GetStatus.md)|擷取已開啟文件的狀態，或在靜態版本，擷取指定檔案 \(靜態，虛擬函式 \(Virtual Function\) 的狀態。|  
|[CFile::LockRange](../Topic/CFile::LockRange.md)|鎖定位元組範圍在檔案中。|  
|[CFile::Open](../Topic/CFile::Open.md)|安全地開啟具有錯誤測試選取的檔案。|  
|[CFile::Read](../Topic/CFile::Read.md)|讀取 \(無緩衝區的\) 資料從檔案中目前的檔案位置。|  
|[CFile::Remove](../Topic/CFile::Remove.md)|刪除指定的檔案 \(靜態函式\)。|  
|[CFile::Rename](../Topic/CFile::Rename.md)|寫入指定的檔案 \(靜態函式\) 重新命名。|  
|[CFile::Seek](../Topic/CFile::Seek.md)|將目前資料指標。|  
|[CFile::SeekToBegin](../Topic/CFile::SeekToBegin.md)|在檔案的開頭、目前資料指標。|  
|[CFile::SeekToEnd](../Topic/CFile::SeekToEnd.md)|將目前資料指標位於檔案結尾。|  
|[CFile::SetFilePath](../Topic/CFile::SetFilePath.md)|設定選取之檔案的完整檔案路徑。|  
|[CFile::SetLength](../Topic/CFile::SetLength.md)|變更檔案的長度。|  
|[CFile::SetStatus](../Topic/CFile::SetStatus.md)|設定指定檔案 \(靜態，虛擬函式 \(Virtual Function\) 的狀態。|  
|[CFile::UnlockRange](../Topic/CFile::UnlockRange.md)|開啟位元組範圍在檔案中。|  
|[CFile::Write](../Topic/CFile::Write.md)|在檔案中並無緩衝區的\) 資料寫入至目前的檔案位置。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CFile::operator HANDLE](../Topic/CFile::operator%20HANDLE.md)|為 `CFile` 物件的控制代碼。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFile::hFileNull](../Topic/CFile::hFileNull.md)|判斷 `CFile` 物件是否具有有效的控制代碼。|  
|[CFile::m\_hFile](../Topic/CFile::m_hFile.md)|通常包含作業系統檔案控制代碼。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CFile::m\_pTM](../Topic/CFile::m_pTM.md)|為 `CAtlTransactionManager` 物件的指標。|  
  
## 備註  
 它會直接提供非緩衝區，二進位磁碟輸入\/輸出服務，，然後透過其衍生類別間接支援文字檔案和記憶體檔案。  使用支援 Microsoft Foundation Class 的序列化 `CArchive` 類別結合的`CFile` 運用。  
  
 這個類別和其衍生類別之間的階層式關聯性可讓您的程式可以透過多型 `CFile` 介面操作任何檔案物件。  記憶體中的檔案，例如，就像是磁碟檔案。  
  
 會提供通用磁碟 I\/O 使用 `CFile` 和它的衍生類別。  提供格式化文字使用 `ofstream` 或其他 Microsoft iostream 類別傳送至磁碟檔案。  
  
 通常，磁碟檔案中 `CFile` 架構會在終結時自動開啟和關閉。  靜態成員函式讓您查詢檔案的狀態，而不需開啟該檔案。  
  
 如需使用 `CFile`的詳細資訊，請參閱《 *執行階段程式庫參考的*文件 [MFC 中的檔案](../../mfc/files-in-mfc.md) 和 [檔案處理](../../c-runtime-library/file-handling.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [MFC 範例 DRAWCLI](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CStdioFile Class](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [如何?:使用 C 檔案類別?](http://go.microsoft.com/fwlink/?LinkId=128046)
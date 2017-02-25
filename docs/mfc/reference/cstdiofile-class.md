---
title: "CStdioFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStdioFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStdioFile class"
  - "I/O [MFC], stream"
  - "stream I/O"
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CStdioFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示 C\+\+. 執行階段資料流檔案為開啟執行階段函式 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
## 語法  
  
```  
class CStdioFile : public CFile  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CStdioFile::CStdioFile](../Topic/CStdioFile::CStdioFile.md)|從路徑或檔案指標的 `CStdioFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CStdioFile::Open](../Topic/CStdioFile::Open.md)|多載。  開放式是專為與 `CStdioFile` 預設建構函式的使用 \(覆寫 [CFile::Open](../Topic/CFile::Open.md)\)。|  
|[CStdioFile::ReadString](../Topic/CStdioFile::ReadString.md)|讀取一行文字。|  
|[CStdioFile::Seek](../Topic/CStdioFile::Seek.md)|將目前資料指標。|  
|[CStdioFile::WriteString](../Topic/CStdioFile::WriteString.md)|寫入一行文字。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CStdioFile::m\_pStream](../Topic/CStdioFile::m_pStream.md)|含有指向開啟檔案。|  
  
## 備註  
 資料流檔案在文字模式 \(預設值\) 或二進位模式會放入緩衝區中並可開啟。  
  
 文字模式為歸位字元和換行字元的字元為提供特殊處理。  當您寫入文字模式 `CStdioFile` 物件寫入新行字元 \(0x0A\) 時，該位元組至 \(0x0D， 0x0A\) 傳送至檔案。  當您讀取時，該位元組至 \(0x0D， 0x0A\) 轉譯為單一 0x0A 位元組。  
  
 [C 檔案](../../mfc/reference/cfile-class.md) 函式 [複製](../Topic/CFile::Duplicate.md)， [LockRange](../Topic/CFile::LockRange.md)， [UnlockRange](../Topic/CFile::UnlockRange.md) ，且不會為 `CStdioFile`支援。  
  
 如果您呼叫在 `CStdioFile`的這些函式，就會 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如需使用 `CStdioFile`的詳細資訊，請參閱《 *執行階段程式庫參考的*文件 [MFC 中的檔案](../../mfc/files-in-mfc.md) 和 [檔案處理](../../c-runtime-library/file-handling.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## 需求  
 **Header:** afx.h  
  
## 請參閱  
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile Class](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../Topic/CFile::Duplicate.md)   
 [CFile::LockRange](../Topic/CFile::LockRange.md)   
 [CFile::UnlockRange](../Topic/CFile::UnlockRange.md)   
 [CNotSupportedException Class](../../mfc/reference/cnotsupportedexception-class.md)   
 [如何?:使用 C 檔案類別?](http://go.microsoft.com/fwlink/?LinkId=128046)
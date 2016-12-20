---
title: "CSharedFile Class | Microsoft Docs"
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
  - "CSharedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSharedFile class"
  - "memory files"
  - "shared memory files"
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSharedFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMemFile](../../mfc/reference/cmemfile-class.md)\-支援共用記憶體檔案的衍生類別。  
  
## 語法  
  
```  
class CSharedFile : public CMemFile  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CSharedFile::CSharedFile](../Topic/CSharedFile::CSharedFile.md)|建構 `CSharedFile` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CSharedFile::Detach](../Topic/CSharedFile::Detach.md)|關閉共用記憶體檔案並將其存放區的控制代碼。|  
|[CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md)|附加共用記憶體檔案至存放區。|  
  
## 備註  
 記憶體檔案的行為就像磁碟檔案，但檔案在 RAM 儲存 \(而非從磁碟。  記憶體檔案是用來快速的暫時儲存區或適合傳送未經處理的位元組或還原序列化的物件在個別處理序之間。  
  
 共用記憶體檔案從該記憶體的其他記憶體檔案與其配置的 [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) Windows 函式。  `CSharedFile` 類別位於全域配置的記憶體區塊儲存資料 \(使用建立 **GlobalAlloc**\)，使用 DDE、剪貼簿，或其他工具一致的資料傳輸作業，使用 `IDataObject`，，且此記憶體區域可以共用，例如，。  
  
 **GlobalAlloc** 傳回 `HGLOBAL` 控制代碼 \(而不是指向記憶體，例如 [malloc](../../c-runtime-library/reference/malloc.md)傳回的指標。  `HGLOBAL` 控制代碼在某些應用程式需要。  例如，將資料保留在剪貼簿上需要 `HGLOBAL` 控制代碼。  
  
 請注意 `CSharedFile` 不使用記憶體對應檔案，，而且不能直接在處理序之間共用。  
  
 `CSharedFile` 物件可以自動配置自己的記憶體或能夠附加至您的記憶體區塊加入至 `CSharedFile` 物件藉由呼叫 [CSharedFile::SetHandle](../Topic/CSharedFile::SetHandle.md)。  在任何情況下， `nGrowBytes` ，如果不是零，成長的記憶體檔案記憶體中 `nGrowBytes`大小將自動配置。  
  
 如需詳細資訊，請參閱《 *執行階段程式庫參考的*文件 [MFC 中的檔案](../../mfc/files-in-mfc.md) 和 [檔案處理](../../c-runtime-library/file-handling.md) 。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [C 檔案](../../mfc/reference/cfile-class.md)  
  
 [CMemFile](../../mfc/reference/cmemfile-class.md)  
  
 `CSharedFile`  
  
## 需求  
 **Header:** afxadv.h  
  
## 請參閱  
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CMemFile Class](../../mfc/reference/cmemfile-class.md)   
 [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574)   
 [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579)   
 [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590)
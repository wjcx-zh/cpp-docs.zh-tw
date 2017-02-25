---
title: "CAtlFile Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlFile"
  - "ATL::CAtlFile"
  - "ATL.CAtlFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlFile class"
ms.assetid: 93ed160b-af2a-448c-9cbe-e5fa46c199bb
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CAtlFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會在檔案處理 API 提供的視窗周圍的小型包裝函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAtlFile : public CHandle  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlFile::CAtlFile](../Topic/CAtlFile::CAtlFile.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlFile::Create](../Topic/CAtlFile::Create.md)|呼叫這個方法會建立或開啟檔案。|  
|[CAtlFile::Flush](../Topic/CAtlFile::Flush.md)|呼叫這個方法會清除檔案的緩衝區和造成任何緩衝資料都寫入檔案。|  
|[CAtlFile::GetOverlappedResult](../Topic/CAtlFile::GetOverlappedResult.md)|呼叫這個方法會取得重疊作業的結果在檔案中。|  
|[CAtlFile::GetPosition](../Topic/CAtlFile::GetPosition.md)|呼叫這個方法會從檔案取得目前資料指標位置。|  
|[CAtlFile::GetSize](../Topic/CAtlFile::GetSize.md)|呼叫這個方法會取得檔案的大小 \(以位元組為單位\)。|  
|[CAtlFile::LockRange](../Topic/CAtlFile::LockRange.md)|呼叫這個方法會鎖定檔案的本機防止其他處理序存取它。|  
|[CAtlFile::Read](../Topic/CAtlFile::Read.md)|呼叫這個方法會將資料從起始在這個位置的檔案\) 將檔案指標。|  
|[CAtlFile::Seek](../Topic/CAtlFile::Seek.md)|呼叫這個方法會將檔案的資料指標。|  
|[CAtlFile::SetSize](../Topic/CAtlFile::SetSize.md)|呼叫這個方法會將檔案的大小。|  
|[CAtlFile::UnlockRange](../Topic/CAtlFile::UnlockRange.md)|呼叫這個方法會解除鎖定檔案的區域。|  
|[CAtlFile::Write](../Topic/CAtlFile::Write.md)|呼叫這個方法會將資料寫入開始在這個位置的檔案\) 將檔案指標。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlFile::m\_pTM](../Topic/CAtlFile::m_pTM.md)|為 `CAtlTransactionManager` 物件的指標。|  
  
## 備註  
 與 Windows API 所需使用此類別，在檔案處理需要時相當簡單，不過，更抽象，，但未包含 MFC 相依性。  
  
## 繼承階層架構  
 [CHandle](../../atl/reference/chandle-class.md)  
  
 `CAtlFile`  
  
## 需求  
 **Header:** atlfile.h  
  
## 請參閱  
 [Marquee 範例](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CHandle Class](../../atl/reference/chandle-class.md)
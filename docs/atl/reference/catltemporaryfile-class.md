---
title: "CAtlTemporaryFile Class | Microsoft Docs"
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
  - "CAtlTemporaryFile"
  - "ATL.CAtlTemporaryFile"
  - "ATL::CAtlTemporaryFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTemporaryFile class"
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 18
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlTemporaryFile Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供方法來為暫存檔的建立和使用。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CAtlTemporaryFile  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md)|建構函式。|  
|[CAtlTemporaryFile::~CAtlTemporaryFile](../Topic/CAtlTemporaryFile::~CAtlTemporaryFile.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTemporaryFile::Close](../Topic/CAtlTemporaryFile::Close.md)|呼叫這個方法會關閉暫存檔案和刪除其內容或將它們儲存在指定的檔案名稱的下方。|  
|[CAtlTemporaryFile::Create](../Topic/CAtlTemporaryFile::Create.md)|呼叫這個方法會建立暫存檔案。|  
|[CAtlTemporaryFile::Flush](../Topic/CAtlTemporaryFile::Flush.md)|呼叫這個方法會強制保持在檔案緩衝區的資料都會寫入至暫存檔。|  
|[CAtlTemporaryFile::GetPosition](../Topic/CAtlTemporaryFile::GetPosition.md)|呼叫這個方法會取得目前資料指標位置。|  
|[CAtlTemporaryFile::GetSize](../Topic/CAtlTemporaryFile::GetSize.md)|呼叫這個方法會取得大小在暫存檔案的位元組。|  
|[CAtlTemporaryFile::HandsOff](../Topic/CAtlTemporaryFile::HandsOff.md)|呼叫這個方法分開 `CAtlTemporaryFile` 物件的檔案。|  
|[CAtlTemporaryFile::HandsOn](../Topic/CAtlTemporaryFile::HandsOn.md)|呼叫這個方法開啟現有的暫存檔並將游標放在位於檔案結尾。|  
|[CAtlTemporaryFile::LockRange](../Topic/CAtlTemporaryFile::LockRange.md)|呼叫這個方法會鎖定檔案的本機防止其他處理序存取它。|  
|[CAtlTemporaryFile::Read](../Topic/CAtlTemporaryFile::Read.md)|呼叫這個方法會將資料從開始在這個位置的暫存檔\) 將檔案指標。|  
|[CAtlTemporaryFile::Seek](../Topic/CAtlTemporaryFile::Seek.md)|呼叫這個方法會將暫存檔的資料指標。|  
|[CAtlTemporaryFile::SetSize](../Topic/CAtlTemporaryFile::SetSize.md)|呼叫這個方法會設定暫存檔案的大小。|  
|[CAtlTemporaryFile::TempFileName](../Topic/CAtlTemporaryFile::TempFileName.md)|呼叫這個方法會傳回暫存檔案的名稱。|  
|[CAtlTemporaryFile::UnlockRange](../Topic/CAtlTemporaryFile::UnlockRange.md)|呼叫這個方法會解除鎖定暫存檔的區域。|  
|[CAtlTemporaryFile::Write](../Topic/CAtlTemporaryFile::Write.md)|呼叫這個方法會將資料寫入開始在這個位置的暫存檔\) 將檔案指標。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTemporaryFile::operator HANDLE](../Topic/CAtlTemporaryFile::operator%20HANDLE.md)|將控制代碼傳回至暫存檔案。|  
  
## 備註  
 `CAtlTemporaryFile` 可以很容易地建立及使用暫存檔案。  名為的檔案，請開啟，會自動關閉，並刪除。  如果需要檔案內容，在檔案關閉之後，可以儲存至具有指定之名稱的新檔案。  
  
## 需求  
 **Header:** atlfile.h  
  
## 範例  
 [CAtlTemporaryFile::CAtlTemporaryFile](../Topic/CAtlTemporaryFile::CAtlTemporaryFile.md)。請參閱範例。  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [CAtlFile Class](../../atl/reference/catlfile-class.md)
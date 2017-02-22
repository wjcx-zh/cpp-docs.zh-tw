---
title: "CAtlTransactionManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAtlTransactionManager"
  - "atltransactionmanager/ATL::CAtlTransactionManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlTransactionManager class"
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CAtlTransactionManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CAtlTransactionManager 類別提供包裝函式為核心交易管理員 \(KTM\) 函式。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
class CAtlTransactionManager;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTransactionManager::~CAtlTransactionManager](../Topic/CAtlTransactionManager::~CAtlTransactionManager.md)|CAtlTransactionManager 解構函式。|  
|[CAtlTransactionManager::CAtlTransactionManager](../Topic/CAtlTransactionManager::CAtlTransactionManager.md)|CAtlTransactionManager 建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTransactionManager::Close](../Topic/CAtlTransactionManager::Close.md)|結束一個交易控制代碼。|  
|[CAtlTransactionManager::Commit](../Topic/CAtlTransactionManager::Commit.md)|認可交易的要求。|  
|[CAtlTransactionManager::Create](../Topic/CAtlTransactionManager::Create.md)|建立交易的控制代碼。|  
|[CAtlTransactionManager::CreateFile](../Topic/CAtlTransactionManager::CreateFile.md)|建立或開啟檔案、資料流或檔案目錄做為交易式作業。|  
|[CAtlTransactionManager::DeleteFile](../Topic/CAtlTransactionManager::DeleteFile.md)|刪除現有檔案當做交易式作業。|  
|[CAtlTransactionManager::FindFirstFile](../Topic/CAtlTransactionManager::FindFirstFile.md)|在目錄中搜尋檔案或子目錄中當做交易作業。|  
|[CAtlTransactionManager::GetFileAttributes](../Topic/CAtlTransactionManager::GetFileAttributes.md)|若要擷取指定檔案或目錄之檔案系統屬性為可交易的作業。|  
|[CAtlTransactionManager::GetFileAttributesEx](../Topic/CAtlTransactionManager::GetFileAttributesEx.md)|若要擷取指定檔案或目錄之檔案系統屬性為可交易的作業。|  
|[CAtlTransactionManager::GetHandle](../Topic/CAtlTransactionManager::GetHandle.md)|傳回交易控制代碼。|  
|[CAtlTransactionManager::IsFallback](../Topic/CAtlTransactionManager::IsFallback.md)|判斷後援呼叫是否啟用。|  
|[CAtlTransactionManager::MoveFile](../Topic/CAtlTransactionManager::MoveFile.md)|移動現有檔案或目錄，包括其子系，是交易作業。|  
|[CAtlTransactionManager::RegCreateKeyEx](../Topic/CAtlTransactionManager::RegCreateKeyEx.md)|建立指定之登錄機碼並將它與交易。  如果機碼已經存在，函式將它開啟。|  
|[CAtlTransactionManager::RegDeleteKey](../Topic/CAtlTransactionManager::RegDeleteKey.md)|刪除子機碼和值從登錄中指定的平台特定檢視中當做交易作業。|  
|[CAtlTransactionManager::RegOpenKeyEx](../Topic/CAtlTransactionManager::RegOpenKeyEx.md)|開啟指定的登錄機碼並將它與交易。|  
|[CAtlTransactionManager::Rollback](../Topic/CAtlTransactionManager::Rollback.md)|復原交易的要求。|  
|[CAtlTransactionManager::SetFileAttributes](../Topic/CAtlTransactionManager::SetFileAttributes.md)|將檔案或目錄的屬性做為交易式作業。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlTransactionManager::m\_bFallback](../Topic/CAtlTransactionManager::m_bFallback.md)|`TRUE` ，如果後援支援，否則 `FALSE` 。|  
|[CAtlTransactionManager::m\_hTransaction](../Topic/CAtlTransactionManager::m_hTransaction.md)|交易的控制代碼。|  
  
## 備註  
  
## 繼承階層架構  
 [ATL::CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)  
  
## 需求  
 **Header:** atltransactionmanager.h  
  
## 請參閱  
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)
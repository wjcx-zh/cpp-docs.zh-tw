---
title: "CComApartment Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComApartment"
  - "CComApartment"
  - "ATL.CComApartment"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartments in ATL EXE modules"
  - "CComApartment class"
ms.assetid: dbc177d7-7ee4-45f2-b563-d578a467ca93
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CComApartment Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供管理在一個執行緒合併模組的 EXE 的單一執行緒 Apartment 的支援。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
class CComApartment  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComApartment::CComApartment](../Topic/CComApartment::CComApartment.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComApartment::Apartment](../Topic/CComApartment::Apartment.md)|標記執行緒的起始位址。|  
|[CComApartment::GetLockCount](../Topic/CComApartment::GetLockCount.md)|會傳回執行緒的目前鎖定計數。|  
|[CComApartment::Lock](../Topic/CComApartment::Lock.md)|將執行緒的鎖定計數。|  
|[CComApartment::Unlock](../Topic/CComApartment::Unlock.md)|減少執行緒的鎖定計數。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComApartment::m\_dwThreadID](../Topic/CComApartment::m_dwThreadID.md)|包含執行緒的識別項。|  
|[CComApartment::m\_hThread](../Topic/CComApartment::m_hThread.md)|包含執行緒的控制代碼。|  
|[CComApartment::m\_nLockCnt](../Topic/CComApartment::m_nLockCnt.md)|包含執行緒目前的鎖定計數。|  
  
## 備註  
 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 用來`CComApartment` 處理在執行緒集區的 EXE 模組的單一執行緒 Apartment。  `CComApartment` 為遞增和遞減鎖定計數的方法給執行緒。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
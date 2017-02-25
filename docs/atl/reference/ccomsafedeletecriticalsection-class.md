---
title: "CComSafeDeleteCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComSafeDeleteCriticalSection"
  - "ATL::CComSafeDeleteCriticalSection"
  - "ATL.CComSafeDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeDeleteCriticalSection class"
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CComSafeDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供用於取得和釋放關鍵區段物件擁有權的方法。  
  
## 語法  
  
```  
  
class CComSafeDeleteCriticalSection : public CComCriticalSection  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection.md)|建構函式。|  
|[CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection](../Topic/CComSafeDeleteCriticalSection::~CComSafeDeleteCriticalSection.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComSafeDeleteCriticalSection::Init](../Topic/CComSafeDeleteCriticalSection::Init.md)|建立和初始化關鍵區段物件。|  
|[CComSafeDeleteCriticalSection::Lock](../Topic/CComSafeDeleteCriticalSection::Lock.md)|取得關鍵區段物件的擁有權。|  
|[CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md)|版本關鍵區段使用的系統資源的物件。|  
  
### 資料成員  
  
|||  
|-|-|  
|[m\_bInitialized](../Topic/CComSafeDeleteCriticalSection::m_bInitialized.md)|旗標內部 **CRITICAL\_SECTION** 物件是否已初始化。|  
  
## 備註  
 `CComSafeDeleteCriticalSection` 從類別 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)衍生。  不過，在 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)`CComSafeDeleteCriticalSection` 提供額外的安全性組態。  
  
 當 `CComSafeDeleteCriticalSection` 執行個體超出範圍或從記憶體中明確地刪除，基礎關鍵區段物件會自動清除，如果它是有效的。  此外，如果基礎，關鍵區段物件從記憶體中，不會配置或已經釋放 [CComSafeDeleteCriticalSection::Term](../Topic/CComSafeDeleteCriticalSection::Term.md) 方法會適當地結束。  
  
 請參閱 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 有關關鍵區段 Helper 類別的詳細資訊。  
  
## 繼承階層架構  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComSafeDeleteCriticalSection`  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
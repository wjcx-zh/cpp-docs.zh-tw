---
title: "CComCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComCriticalSection"
  - "CComCriticalSection"
  - "ATL::CComCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCriticalSection class"
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供用於取得和釋放關鍵區段物件擁有權的方法。  
  
## 語法  
  
```  
  
class CComCriticalSection  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComCriticalSection::CComCriticalSection](../Topic/CComCriticalSection::CComCriticalSection.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCriticalSection::Init](../Topic/CComCriticalSection::Init.md)|建立和初始化關鍵區段物件。|  
|[CComCriticalSection::Lock](../Topic/CComCriticalSection::Lock.md)|取得關鍵區段物件的擁有權。|  
|[CComCriticalSection::Term](../Topic/CComCriticalSection::Term.md)|版本關鍵區段使用的系統資源的物件。|  
|[CComCriticalSection::Unlock](../Topic/CComCriticalSection::Unlock.md)|釋放關鍵區段物件的擁有權。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComCriticalSection::m\_sec](../Topic/CComCriticalSection::m_sec.md)|**CRITICAL\_SECTION** 物件。|  
  
## 備註  
 `CComCriticalSection` 類似類別 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)，不過，您必須明確地初始化和釋放關鍵區段。  
  
 一般而言，您會 `typedef` 名稱 [CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)使用 `CComCriticalSection` 。  這個名稱參考 `CComCriticalSection` ，當使用 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 。  
  
 比起直接呼叫 `Lock` 和 `Unlock` 參閱 [CComCritSecLock 類別](../../atl/reference/ccomcritseclock-class.md) 為了更安全的方式使用這個類別。  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCritSecLock Class](../../atl/reference/ccomcritseclock-class.md)
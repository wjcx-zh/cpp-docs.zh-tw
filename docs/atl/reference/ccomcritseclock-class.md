---
title: "CComCritSecLock Class | Microsoft Docs"
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
  - "ATL::CComCritSecLock"
  - "ATL.CComCritSecLock<TLock>"
  - "ATL::CComCritSecLock<TLock>"
  - "ATL.CComCritSecLock"
  - "CComCritSecLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComCritSecLock class"
ms.assetid: 223152a1-86c3-4ef9-89a7-f455fe791b0e
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComCritSecLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供的鎖定和解除鎖定關鍵區段物件所提供的方法。  
  
## 語法  
  
```  
  
      template<  
   class TLock  
> class CComCritSecLock  
```  
  
#### 參數  
 *TLock*  
 將鎖定和解除鎖定的物件。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComCritSecLock::CComCritSecLock](../Topic/CComCritSecLock::CComCritSecLock.md)|建構函式。|  
|[CComCritSecLock::~CComCritSecLock](../Topic/CComCritSecLock::~CComCritSecLock.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComCritSecLock::Lock](../Topic/CComCritSecLock::Lock.md)|呼叫這個方法會鎖定關鍵區段物件。|  
|[CComCritSecLock::Unlock](../Topic/CComCritSecLock::Unlock.md)|呼叫這個方法會解除鎖定關鍵區段物件。|  
  
## 備註  
 使用這個類別來鎖定及解除鎖定物件以更安全的方式與 [CComCriticalSection 類別](../../atl/reference/ccomcriticalsection-class.md) 或 [CComAutoCriticalSection 類別](../../atl/reference/ccomautocriticalsection-class.md)。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)
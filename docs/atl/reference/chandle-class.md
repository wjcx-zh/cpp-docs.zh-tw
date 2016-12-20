---
title: "CHandle Class | Microsoft Docs"
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
  - "ATL.CHandle"
  - "ATL::CHandle"
  - "CHandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHandle class"
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHandle Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供方法來建立和使用物件控制代碼。  
  
## 語法  
  
```  
  
class CHandle  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHandle::CHandle](../Topic/CHandle::CHandle.md)|建構函式。|  
|[CHandle::~CHandle](../Topic/CHandle::~CHandle.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHandle::Attach](../Topic/CHandle::Attach.md)|呼叫這個方法附加至現有的控制代碼的 `CHandle` 物件。|  
|[CHandle::Close](../Topic/CHandle::Close.md)|呼叫這個方法會關閉 `CHandle` 物件。|  
|[CHandle::Detach](../Topic/CHandle::Detach.md)|呼叫這個方法中斷連結 `CHandle` 物件的控制代碼。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CHandle::operator HANDLE](../Topic/CHandle::operator%20HANDLE.md)|傳回已儲存的控制代碼的值。|  
|[CHandle::operator \=](../Topic/CHandle::operator%20=.md)|指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CHandle::m\_h](../Topic/CHandle::m_h.md)|儲存控制項的成員變數。|  
  
## 備註  
 可以使用 `CHandle` 物件，就需要控制代碼:主要差異是 `CHandle` 物件會自動刪除。  
  
> [!NOTE]
>  而其他使用 INVALID\_HANDLE\_VALUE，有些 API 函式會使用 null 做為 null 或無效的控制代碼。  只`CHandle` 用法可讓和視為 INVALID\_HANDLE\_VALUE 失效為真正的控制代碼。  如果您呼叫可能會傳回 INVALID\_HANDLE\_VALUE 的 API，您應該檢查這個值是在呼叫 [CHandle::Attach](../Topic/CHandle::Attach.md) 或將它傳遞至 `CHandle` 建構函式並傳遞 null。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
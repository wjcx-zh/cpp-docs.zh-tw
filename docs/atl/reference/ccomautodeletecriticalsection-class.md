---
title: "CComAutoDeleteCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComAutoDeleteCriticalSection"
  - "CComAutoDeleteCriticalSection"
  - "ATL::CComAutoDeleteCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoDeleteCriticalSection class"
ms.assetid: 2396dbea-1c60-4841-b50e-c4e18af311a3
caps.latest.revision: 17
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAutoDeleteCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別提供用於取得和釋放關鍵區段物件擁有權的方法。  
  
## 語法  
  
```  
  
class CComAutoDeleteCriticalSection : public CComSafeDeleteCriticalSection  
  
```  
  
## 備註  
 `CComAutoDeleteCriticalSection` 從類別 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)衍生。  不過， `CComAutoDeleteCriticalSection` 覆寫 [詞彙](../Topic/CComSafeDeleteCriticalSection::Term.md) 方法為 `private` 存取權，強制記憶體清除發生，但這個類別的執行個體超出範圍或從記憶體時明確刪除。  
  
 這個類別不會在其基底類別的其他方法。  請參閱 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md) 和 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 有關關鍵區段 Helper 類別的詳細資訊。  
  
## 繼承階層架構  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)  
  
 `CComAutoDeleteCriticalSection`  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CComSafeDeleteCriticalSection Class](../../atl/reference/ccomsafedeletecriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
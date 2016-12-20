---
title: "CComFakeCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComFakeCriticalSection"
  - "CComFakeCriticalSection"
  - "ATL::CComFakeCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComFakeCriticalSection class"
ms.assetid: a4811b97-96bb-493b-ab9f-62822aeddb10
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComFakeCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供方法和 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) ，但不提供關鍵區段。  
  
## 語法  
  
```  
  
class CComFakeCriticalSection  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComFakeCriticalSection::Init](../Topic/CComFakeCriticalSection::Init.md)|因為沒有關鍵區段，則不會執行任何動作。|  
|[CComFakeCriticalSection::Lock](../Topic/CComFakeCriticalSection::Lock.md)|因為沒有關鍵區段，則不會執行任何動作。|  
|[CComFakeCriticalSection::Term](../Topic/CComFakeCriticalSection::Term.md)|因為沒有關鍵區段，則不會執行任何動作。|  
|[CComFakeCriticalSection::Unlock](../Topic/CComFakeCriticalSection::Unlock.md)|因為沒有關鍵區段，則不會執行任何動作。|  
  
## 備註  
 `CComFakeCriticalSection` 反映在 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)找到的方法。  不過， `CComFakeCriticalSection` 不提供關鍵區段，因此，它的方法不會有任何作用。  
  
 一般而言，您會 `typedef` 名稱使用 `CComFakeCriticalSection` ， `AutoCriticalSection` 或 `CriticalSection`。  當使用 [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) 或 [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)，這兩個 `typedef` 名稱參考 `CComFakeCriticalSection`時。  當使用 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)時，它們會參考 [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md) 和 `CComCriticalSection`，名稱分別為、和。  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
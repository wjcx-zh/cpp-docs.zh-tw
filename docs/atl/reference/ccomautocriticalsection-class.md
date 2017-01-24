---
title: "CComAutoCriticalSection Class | Microsoft Docs"
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
  - "ATL.CComAutoCriticalSection"
  - "ATL::CComAutoCriticalSection"
  - "CComAutoCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAutoCriticalSection class"
ms.assetid: 491a9d90-3398-4f90-88f5-fd2172a46b30
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAutoCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComAutoCriticalSection` 用於取得和釋放關鍵區段物件擁有權的方法。  
  
## 語法  
  
```  
  
class CComAutoCriticalSection : public CComCriticalSection  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComAutoCriticalSection::CComAutoCriticalSection](../Topic/CComAutoCriticalSection::CComAutoCriticalSection.md)|建構函式。|  
|[CComAutoCriticalSection::~CComAutoCriticalSection](../Topic/CComAutoCriticalSection::~CComAutoCriticalSection.md)|解構函式。|  
  
## 備註  
 `CComAutoCriticalSection` 類似類別 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)，不同的是， `CComAutoCriticalSection` 自動初始化在建構函式中的關鍵區段物件。  
  
 一般而言，您會 `typedef` 名稱 [AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)使用 `CComAutoCriticalSection` 。  這個名稱參考 `CComAutoCriticalSection` ，當使用 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) 。  
  
 會在使用這個類別時，從 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 的 `Init` 和 `Term` 方法無法使用。  
  
## 繼承階層架構  
 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)  
  
 `CComAutoCriticalSection`  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CComFakeCriticalSection Class](../../atl/reference/ccomfakecriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)
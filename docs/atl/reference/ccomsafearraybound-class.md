---
title: "CComSafeArrayBound Class | Microsoft Docs"
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
  - "ATL.CComSafeArrayBound"
  - "ATL::CComSafeArrayBound"
  - "CComSafeArrayBound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSafeArrayBound class"
ms.assetid: dd6299db-5f84-4630-bbf0-f5add5318437
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSafeArrayBound Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別是 [SAFEARRAYBOUND](http://msdn.microsoft.com/zh-tw/303a9bdb-71d6-4f14-8747-84cf84936c6d) 結構的包裝函式。  
  
## 語法  
  
```  
  
class CComSafeArrayBound : public SAFEARRAYBOUND  
  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[CComSafeArrayBound](../Topic/CComSafeArrayBound::CComSafeArrayBound.md)|建構函式。|  
|[GetCount](../Topic/CComSafeArrayBound::GetCount.md)|呼叫這個方法會傳回項目的數目。|  
|[GetLowerBound](../Topic/CComSafeArrayBound::GetLowerBound.md)|呼叫這個方法會傳回下限。|  
|[GetUpperBound](../Topic/CComSafeArrayBound::GetUpperBound.md)|呼叫這個方法會傳回這個上限。|  
|[SetCount](../Topic/CComSafeArrayBound::SetCount.md)|呼叫這個方法會設定項目的數目。|  
|[SetLowerBound](../Topic/CComSafeArrayBound::SetLowerBound.md)|呼叫這個方法會設定下限。|  
  
### 運算子  
  
|||  
|-|-|  
|[\=運算子](../Topic/CComSafeArrayBound::operator%20=.md)|設定 `CComSafeArrayBound` 設為新值。|  
  
## 備註  
 這個類別是 [CComSafeArray](../../atl/reference/ccomsafearray-class.md)使用的 **SAFEARRAYBOUND** 結構的包裝函式。  它提供查詢提供方法，並將 `CComSafeArray` 的單一維度的上限和下限會和它所包含的項目數目。  多維式 `CComSafeArray` 物件使用陣列 `CComSafeArrayBound` 物件，而每個維度的。  因此，當使用方法，例如 [GetCount](../Topic/CComSafeArrayBound::GetCount.md)時請注意，這個方法不會傳回元素總數多維陣列。  
  
 **Header:** atlsafe.h  
  
## 需求  
 **Header:** atlsafe.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
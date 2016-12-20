---
title: "CComSimpleThreadAllocator Class | Microsoft Docs"
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
  - "CComSimpleThreadAllocator"
  - "ATL::CComSimpleThreadAllocator"
  - "ATL.CComSimpleThreadAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL threads"
  - "ATL threads, 配置"
  - "CComSimpleThreadAllocator class"
  - "執行緒 [ATL], selecting threads"
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSimpleThreadAllocator Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會處理類別的 `CComAutoThreadModule`執行緒選取範圍。  
  
## 語法  
  
```  
  
class CComSimpleThreadAllocator  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComSimpleThreadAllocator::GetThread](../Topic/CComSimpleThreadAllocator::GetThread.md)|選取執行緒。|  
  
## 備註  
 `CComSimpleThreadAllocator` 處理 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)執行緒選取範圍。  `CComSimpleThreadAllocator::GetThread` 傳遞每個執行緒迴圈並傳回下一個序列。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CComApartment Class](../../atl/reference/ccomapartment-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
---
title: "IThreadPoolConfig Interface | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IThreadPoolConfig"
  - "ATL::IThreadPoolConfig"
  - "ATL.IThreadPoolConfig"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IThreadPoolConfig interface"
ms.assetid: 69e642bf-6925-46e6-9a37-cce52231b1cc
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IThreadPoolConfig Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個介面會設定執行緒集區的方法。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]執行的應用程式。  
  
## 語法  
  
```  
  
      __interface  
__declspec(uuid("B1F64757-6E88-4fa2-8886-7848B0D7E660"))  
IThreadPoolConfig :  
public IUnknown  
```  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[GetSize](../Topic/IThreadPoolConfig::GetSize.md)|呼叫這個方法會取得執行緒的數目在集區中。|  
|[GetTimeout](../Topic/IThreadPoolConfig::GetTimeout.md)|以毫秒為單位\) 呼叫這個方法會取得最長時間執行緒集區執行緒等待關閉。|  
|[SetSize](../Topic/IThreadPoolConfig::SetSize.md)|呼叫這個方法會設定執行緒的數目在集區中。|  
|[SetTimeout](../Topic/IThreadPoolConfig::SetTimeout.md)|以毫秒為單位\) 呼叫這個方法會設定最長時間執行緒集區執行緒等待關閉。|  
  
## 備註  
 這個介面是由 [CThreadPool](../../atl/reference/cthreadpool-class.md)實作。  
  
## 需求  
 **Header:** 函式  
  
## 請參閱  
 [類別](../../atl/reference/atl-classes.md)   
 [CThreadPool Class](../../atl/reference/cthreadpool-class.md)
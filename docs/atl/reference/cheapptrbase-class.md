---
title: "CHeapPtrBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHeapPtrBase"
  - "ATL::CHeapPtrBase"
  - "CHeapPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrBase class"
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供數個智慧標籤的堆疊指標類別的基礎。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template <  
class T,  
class Allocator= CCRTAllocator   
> class CHeapPtrBase  
```  
  
#### 參數  
 `T`  
 儲存在堆積上的物件型別。  
  
 `Allocator`  
 要使用的記憶體配置類別。  預設 CRT 偵錯堆積常式所需配置和釋放記憶體。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrBase::~CHeapPtrBase](../Topic/CHeapPtrBase::~CHeapPtrBase.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrBase::AllocateBytes](../Topic/CHeapPtrBase::AllocateBytes.md)|呼叫這個方法會配置記憶體。|  
|[CHeapPtrBase::Attach](../Topic/CHeapPtrBase::Attach.md)|呼叫這個方法會接受一個現有指標的擁有權。|  
|[CHeapPtrBase::Detach](../Topic/CHeapPtrBase::Detach.md)|呼叫這個方法會釋放指標的擁有權。|  
|[CHeapPtrBase::Free](../Topic/CHeapPtrBase::Free.md)|呼叫這個方法會刪除上的物件。 `CHeapPtrBase`。|  
|[CHeapPtrBase::ReallocateBytes](../Topic/CHeapPtrBase::ReallocateBytes.md)|呼叫這個方法會重新配置記憶體。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrBase::operator T\*](../Topic/CHeapPtrBase::operator%20T*.md)|轉型運算子。|  
|[CHeapPtrBase::operator &](../Topic/CHeapPtrBase::operator%20&.md)|\_& 運算子。|  
|[CHeapPtrBase::operator \-\>](../Topic/CHeapPtrBase::operator%20-%3E.md)|成員指標運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CHeapPtrBase::m\_pData](../Topic/CHeapPtrBase::m_pData.md)|指標資料成員變數。|  
  
## 備註  
 這個類別會提供數個智慧標籤的堆疊指標類別的基礎。  衍生類別，例如， [CHeapPtr](../../atl/reference/cheapptr-class.md) 和 [CComHeapPtr](../../atl/reference/ccomheapptr-class.md)，加入自己的建構函式和運算子。  在實作中看到這些類別。  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
---
title: "CAutoVectorPtr Class | Microsoft Docs"
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
  - "ATL::CAutoVectorPtr"
  - "ATL.CAutoVectorPtr"
  - "ATL.CAutoVectorPtr<T>"
  - "CAutoVectorPtr"
  - "ATL::CAutoVectorPtr<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAutoVectorPtr class"
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoVectorPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用向量新增和刪除運算子，這個類別表示智慧型指標物件。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
typename T  
> class CAutoVectorPtr  
```  
  
#### 參數  
 `T`  
 指標型別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAutoVectorPtr::CAutoVectorPtr](../Topic/CAutoVectorPtr::CAutoVectorPtr.md)|建構函式。|  
|[CAutoVectorPtr::~CAutoVectorPtr](../Topic/CAutoVectorPtr::~CAutoVectorPtr.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAutoVectorPtr::Allocate](../Topic/CAutoVectorPtr::Allocate.md)|呼叫這個方法會配置 `CAutoVectorPtr`點的部分需要的記憶體中的物件。|  
|[CAutoVectorPtr::Attach](../Topic/CAutoVectorPtr::Attach.md)|呼叫這個方法會接受一個現有指標的擁有權。|  
|[CAutoVectorPtr::Detach](../Topic/CAutoVectorPtr::Detach.md)|呼叫這個方法會釋放指標的擁有權。|  
|[CAutoVectorPtr::Free](../Topic/CAutoVectorPtr::Free.md)|呼叫這個方法會刪除上的物件。 `CAutoVectorPtr`。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CAutoVectorPtr::operator T \*](../Topic/CAutoVectorPtr::operator%20T%20*.md)|轉型運算子。|  
|[CAutoVectorPtr::operator \=](../Topic/CAutoVectorPtr::operator%20=.md)|指派運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAutoVectorPtr::m\_p](../Topic/CAutoVectorPtr::m_p.md)|指標資料成員變數。|  
  
## 備註  
 這個類別會建立和管理的智慧型指標提供方法，可協助防止記憶體遺漏 \(Memory Leak\) 會自動釋放資源，並在超出範圍時。  `CAutoVectorPtr` 類似 `CAutoPtr`，這是唯一的差異如下 `CAutoVectorPtr` 使用 [vector new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) 和 [向量 delete &#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 配置和釋放記憶體而不是 C\+\+ **new** 和 **刪除** 運算子。  如果有需要，請參閱 [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)`CAutoVectorPtr` 集合類別。  
  
 提供的使用範例的智慧型指標 \(請參閱類別 [CAutoPtr](../../atl/reference/cautoptr-class.md) 。  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CAutoPtr Class](../../atl/reference/cautoptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
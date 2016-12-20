---
title: "CComObjectStack Class | Microsoft Docs"
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
  - "ATL::CComObjectStack"
  - "ATL.CComObjectStack"
  - "ATL::CComObjectStack<Base>"
  - "ATL.CComObjectStack<Base>"
  - "CComObjectStack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectStack class"
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectStack Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會建立暫存的 COM 物件並提供 **IUnknown**的基本架構實作。  
  
## 語法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectStack :  
   public Base  
```  
  
#### 參數  
 `Base`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectStack::CComObjectStack](../Topic/CComObjectStack::CComObjectStack.md)|建構函式。|  
|[CComObjectStack::~CComObjectStack](../Topic/CComObjectStack::~CComObjectStack.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectStack::AddRef](../Topic/CComObjectStack::AddRef.md)|傳回零。  在偵錯模式中，呼叫 `_ASSERTE`。|  
|[CComObjectStack::QueryInterface](../Topic/CComObjectStack::QueryInterface.md)|傳回 **E\_NOINTERFACE**。  在偵錯模式中，呼叫 `_ASSERTE`。|  
|[CComObjectStack::Release](../Topic/CComObjectStack::Release.md)|傳回零。  在偵錯模式中，呼叫 `_ASSERTE`。  ~|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectStack::m\_hResFinalConstruct](../Topic/CComObjectStack::m_hResFinalConstruct.md)|包含在 `CComObjectStack` 建構物件時所傳回的 **HRESULT** 。|  
  
## 備註  
 `CComObjectStack` 用於建立暫時 COM 物件和物件提供 **IUnknown**的基本架構實作。  一般而言，在一個函式中使用物件，建立區域變數 \(也就是推入到堆疊上\)。  因為終結，當函式執行時，參考計數不會執行提高效率。  
  
 下列範例顯示如何建立 COM 物件用於函式內:  
  
 [!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/CPP/ccomobjectstack-class_1.cpp)]  
  
 當函式完成，暫存物件 `Tempobj` 推入堆疊和自動消失。  
  
## 繼承階層架構  
 `Base`  
  
 `CComObjectStack`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComObjectGlobal Class](../../atl/reference/ccomobjectglobal-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
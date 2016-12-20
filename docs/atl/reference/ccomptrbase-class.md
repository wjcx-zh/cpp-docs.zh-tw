---
title: "CComPtrBase Class | Microsoft Docs"
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
  - "ATL.CComPtrBase"
  - "ATL::CComPtrBase<T>"
  - "ATL.CComPtrBase<T>"
  - "ATL::CComPtrBase"
  - "CComPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtrBase class"
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 COM 架構的記憶體的常式，這個類別提供智慧型指標類別提供了基礎。  
  
## 語法  
  
```  
  
      template <  
   class T   
> class CComPtrBase  
```  
  
#### 參數  
 `T`  
 智慧型指標所參考的物件型別。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComPtrBase::~CComPtrBase](../Topic/CComPtrBase::~CComPtrBase.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)|呼叫這個方法會建立 `CComPtrBase` 的連接點和用戶端的接收之間的連接。|  
|[CComPtrBase::Attach](../Topic/CComPtrBase::Attach.md)|呼叫這個方法會接受一個現有指標的擁有權。|  
|[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)|呼叫這個方法會建立類別的物件與指定的類別 ID 或程式 ID.|  
|[CComPtrBase::CopyTo](../Topic/CComPtrBase::CopyTo.md)|呼叫這個方法會複製 `CComPtrBase` 指標到另一個指標變數。|  
|[CComPtrBase::Detach](../Topic/CComPtrBase::Detach.md)|呼叫這個方法會釋放指標的擁有權。|  
|[CComPtrBase::IsEqualObject](../Topic/CComPtrBase::IsEqualObject.md)|呼叫這個方法會檢查是否為相同的 **IUnknown** 指定的點是否要與 `CComPtrBase` 物件。|  
|[CComPtrBase::QueryInterface](../Topic/CComPtrBase::QueryInterface.md)|呼叫這個方法會傳回指標上指定的介面。|  
|[CComPtrBase::Release](../Topic/CComPtrBase::Release.md)|呼叫這個方法會釋放介面。|  
|[CComPtrBase::SetSite](../Topic/CComPtrBase::SetSite.md)|呼叫這個方法會設定物件的 `CComPtrBase` 網站父物件的 **IUnknown** 的。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CComPtrBase::operator T\*](../Topic/CComPtrBase::operator%20T*.md)|轉型運算子。|  
|[CComPtrBase::operator \!](../Topic/CComPtrBase::operator%20!.md)|NOT 運算子。|  
|[CComPtrBase::operator &](../Topic/CComPtrBase::operator%20&.md)|\_& 運算子。|  
|[CComPtrBase::operator \*](../Topic/CComPtrBase::operator%20*.md)|\*運算子。|  
|[CComPtrBase::operator \<](../Topic/CComPtrBase::operator%20%3C.md)|小於運算子。|  
|[CComPtrBase::operator \=\=](../Topic/CComPtrBase::operator%20==.md)|等號比較運算子。|  
|[CComPtrBase::operator \-\>](../Topic/CComPtrBase::operator%20-%3E.md)|成員指標運算子。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComPtrBase::p](../Topic/CComPtrBase::p.md)|指標資料成員變數。|  
  
## 備註  
 這個類別會使用 COM 記憶體管理常式的其他智慧型指標提供基礎，例如和 [CComQIPtr](../../atl/reference/ccomqiptr-class.md)[CComPtr](../../atl/reference/ccomptr-class.md)。  衍生類別可以加入自己的建構函式和運算子， `CComPtrBase`，但會根據提供的方法。  
  
## 需求  
 **Header:** atlcomcli.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
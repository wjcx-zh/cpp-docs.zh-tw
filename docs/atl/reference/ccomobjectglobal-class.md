---
title: "CComObjectGlobal Class | Microsoft Docs"
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
  - "CComObjectGlobal"
  - "ATL::CComObjectGlobal<Base>"
  - "ATL::CComObjectGlobal"
  - "ATL.CComObjectGlobal"
  - "ATL.CComObjectGlobal<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectGlobal class"
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObjectGlobal Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會處理包含在您的 `Base` 物件的模組的參考次數。  
  
## 語法  
  
```  
  
      template<  
   class Base   
>  
class CComObjectGlobal :  
   public Base  
```  
  
#### 參數  
 `Base`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectGlobal::CComObjectGlobal](../Topic/CComObjectGlobal::CComObjectGlobal.md)|建構函式。|  
|[CComObjectGlobal::~CComObjectGlobal](../Topic/CComObjectGlobal::~CComObjectGlobal.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectGlobal::AddRef](../Topic/CComObjectGlobal::AddRef.md)|實作全域 `AddRef`。|  
|[CComObjectGlobal::QueryInterface](../Topic/CComObjectGlobal::QueryInterface.md)|實作全域 `QueryInterface`。|  
|[CComObjectGlobal::Release](../Topic/CComObjectGlobal::Release.md)|實作全域 **版本**。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComObjectGlobal::m\_hResFinalConstruct](../Topic/CComObjectGlobal::m_hResFinalConstruct.md)|包含在 `CComObjectGlobal` 建構物件時所傳回的 **HRESULT** 。|  
  
## 備註  
 `CComObjectGlobal` 處理包含在您的 `Base` 物件的模組的參考次數。  `CComObjectGlobal` 確保您的物件不會被刪除，只要未釋放模組。  您的物件，當整個模組的參考計數會變成零，則只會移除。  
  
 例如，使用， `CComObjectGlobal`Class Factory，以保留由它的所有用戶端都共用的通用全域物件。  
  
## 繼承階層架構  
 `Base`  
  
 `CComObjectGlobal`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComObjectStack Class](../../atl/reference/ccomobjectstack-class.md)   
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)
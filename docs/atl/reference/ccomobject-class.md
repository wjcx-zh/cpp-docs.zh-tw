---
title: "CComObject Class | Microsoft Docs"
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
  - "ATL.CComObject<Base>"
  - "ATL::CComObject"
  - "ATL::CComObject<Base>"
  - "ATL.CComObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObject class"
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作 nonaggregated 物件的 **IUnknown** 。  
  
## 語法  
  
```  
  
      template<  
   class Base   
>  
class CComObject :  
   public Base  
```  
  
#### 參數  
 `Base`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)，以及從任何其他介面在物件要支援。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComObject::CComObject](../Topic/CComObject::CComObject.md)|建構函式。|  
|[CComObject::~CComObject](../Topic/CComObject::~CComObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComObject::AddRef](../Topic/CComObject::AddRef.md)|將物件的參考計數。|  
|[CComObject::CreateInstance](../Topic/CComObject::CreateInstance.md)|\(靜態\) 建立新的 `CComObject` 物件。|  
|[CComObject::QueryInterface](../Topic/CComObject::QueryInterface.md)|擷取指標所要求的介面。|  
|[CComObject::Release](../Topic/CComObject::Release.md)|遞減物件的參考計數。|  
  
## 備註  
 一 nonaggregated 物件的`CComObject` 實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 。  然而，在 `QueryInterface`、 `AddRef`和 **版本** 的呼叫委派給 `CComObjectRootEx`。  
  
 如需使用 `CComObject`的詳細資訊，請參閱本文 [ATL COM 物件的基本概念](../../atl/fundamentals-of-atl-com-objects.md)。  
  
## 繼承階層架構  
 `Base`  
  
 `CComObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)
---
title: "CComContainedObject Class | Microsoft Docs"
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
  - "CComContainedObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], 在 ATL 中"
  - "aggregation [C++], ATL 物件"
  - "CComContainedObject class"
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComContainedObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作委派 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 給主控物件的 **IUnknown**。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class Base   
>  
class CComContainedObject :  
public Base  
```  
  
#### 參數  
 `Base`  
 您的類別，衍生自 [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) 或 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CComContainedObject::CComContainedObject](../Topic/CComContainedObject::CComContainedObject.md)|建構函式。  初始化成員指標給主控物件的 `IUnknown`。|  
|[CComContainedObject::~CComContainedObject](../Topic/CComContainedObject::~CComContainedObject.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComContainedObject::AddRef](../Topic/CComContainedObject::AddRef.md)|將在主控物件的參考計數。|  
|[CComContainedObject::GetControllingUnknown](../Topic/CComContainedObject::GetControllingUnknown.md)|擷取主控物件的 `IUnknown`。|  
|[CComContainedObject::QueryInterface](../Topic/CComContainedObject::QueryInterface.md)|擷取指標在主控物件需要的介面。|  
|[CComContainedObject::Release](../Topic/CComContainedObject::Release.md)|會在主控物件的參考計數。|  
  
## 備註  
 在 ATL 類別 [CComAggObject](../../atl/reference/ccomaggobject-class.md)、 [CComPolyObject](../../atl/reference/ccompolyobject-class.md)和 [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)使用 `CComContainedObject` 。  `CComContainedObject` 透過委派實作 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 給主控物件的 **IUnknown**。  \(擁有者是彙總的外部物件，或物件 Tear\-Off 介面所建立\)。 `CComContainedObject` 呼叫 `CComObjectRootEx` 的 `OuterQueryInterface`、 `OuterAddRef`和 `OuterRelease`，所有繼承透過 `Base`。  
  
## 繼承階層架構  
 `Base`  
  
 `CComContainedObject`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
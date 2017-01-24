---
title: "CAtlAutoThreadModule Class | Microsoft Docs"
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
  - "ATL.CAtlAutoThreadModule"
  - "CAtlAutoThreadModule"
  - "ATL::CAtlAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlAutoThreadModule class"
ms.assetid: 3be834aa-55ef-403e-94ae-41979691b15f
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作執行緒集區， Apartment Model COM 伺服器。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      class CAtlAutoThreadModule :  
public CAtlAutoThreadModuleT< CAtlAutoThreadModule >  
```  
  
## 備註  
 `CAtlAutoThreadModule` [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) 從衍生並實作執行緒集區， Apartment Model COM 伺服器。  `CAtlAutoThreadModule` 使用 [CComApartment](../../atl/reference/ccomapartment-class.md) 處理每個執行緒的單一執行緒 Apartment 中模組。  
  
 您可以在您的物件類別定義必須使用 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 巨集指定 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 做為 Class Factory。  您應該可以從 `CAtlAutoThreadModuleT` 衍生自類別的單一執行個體 \(例如 `CAtlAutoThreadModule`。  例如：  
  
 `CAtlAutoThreadModule _AtlAutoModule; // name is immaterial.`  
  
> [!NOTE]
>  這個類別會取代過時 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md) 類別。  
  
## 繼承階層架構  
 `IAtlAutoThreadModule`  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 `CAtlAutoThreadModule`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [CAtlAutoThreadModuleT Class](../../atl/reference/catlautothreadmodulet-class.md)   
 [IAtlAutoThreadModule Class](../../atl/reference/iatlautothreadmodule-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
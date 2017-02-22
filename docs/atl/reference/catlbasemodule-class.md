---
title: "CAtlBaseModule Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CAtlBaseModule"
  - "ATL.CAtlBaseModule"
  - "CAtlBaseModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlBaseModule class"
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CAtlBaseModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會在每個 ATL 專案具現化。  
  
## 語法  
  
```  
  
   class CAtlBaseModule :  
public _ATL_BASE_MODULE  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlBaseModule::CAtlBaseModule](../Topic/CAtlBaseModule::CAtlBaseModule.md)|建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlBaseModule::AddResourceInstance](../Topic/CAtlBaseModule::AddResourceInstance.md)|將資源加入至執行個體中儲存的控制代碼的清單。|  
|[CAtlBaseModule::GetHInstanceAt](../Topic/CAtlBaseModule::GetHInstanceAt.md)|將控制代碼傳回至指定的資源執行個體。|  
|[CAtlBaseModule::GetModuleInstance](../Topic/CAtlBaseModule::GetModuleInstance.md)|會傳回從物件的 `CAtlBaseModule` 模組的執行個體。|  
|[CAtlBaseModule::GetResourceInstance](../Topic/CAtlBaseModule::GetResourceInstance.md)|傳回從 `CAtlBaseModule` 物件的資源執行個體。|  
|[CAtlBaseModule::RemoveResourceInstance](../Topic/CAtlBaseModule::RemoveResourceInstance.md)|從已儲存的控制代碼清單移除資源執行個體。|  
|[CAtlBaseModule::SetResourceInstance](../Topic/CAtlBaseModule::SetResourceInstance.md)|設定 `CAtlBaseModule` 物件的資源執行個體。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlBaseModule::m\_bInitFailed](../Topic/CAtlBaseModule::m_bInitFailed.md)|表示的變數初始化模組是否失敗。|  
  
## 備註  
 `CAtlBaseModule` 執行個體命名為 \_AtlBaseModule 存在於每一個 ATL 專案，其中包含控制代碼之模組的執行個體，控制代碼會包含模組根據預設，會是相同的資源 \(和陣列控制代碼提供主要資源的模組。  `CAtlBaseModule` 可以安全地從多執行緒存取。  
  
 這個類別是用來取代舊版的 ATL [CComModule](../../atl/reference/ccommodule-class.md) 過時的類別。  
  
## 繼承階層架構  
 [\_ATL\_BASE\_MODULE](../Topic/_ATL_BASE_MODULE.md)  
  
 `CAtlBaseModule`  
  
## 需求  
 **Header:** atlcore.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
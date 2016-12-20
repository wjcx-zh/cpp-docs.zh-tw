---
title: "CComAutoThreadModule Class | Microsoft Docs"
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
  - "CComAutoThreadModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "apartment model modules"
  - "CComAutoThreadModule class"
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComAutoThreadModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

來自 ATL 7.0， `CComAutoThreadModule` 已經過時:如需的詳細資訊請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
  
      template<  
class ThreadAllocator= CComSimpleThreadAllocator   
>  
class CComAutoThreadModule :  
public CComModule  
```  
  
#### 參數  
 `ThreadAllocator`  
 \[in\] 類別管理執行緒的選取範圍。  預設值為 [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)。  
  
## Members  
  
### 方法  
  
|||  
|-|-|  
|[CreateInstance](../Topic/CComAutoThreadModule::CreateInstance.md)|選取執行緒在它們之間是在關聯的 Apartment 中的物件。|  
|[GetDefaultThreads](../Topic/CComAutoThreadModule::GetDefaultThreads.md)|\(靜態\) 會動態計算執行緒的數目是根據處理器數目的模組。|  
|[\(1183\)](../Topic/CComAutoThreadModule::Init.md)|建立模組的執行緒。|  
|[鎖定](../Topic/CComAutoThreadModule::Lock.md)|將鎖定計數在模組和目前執行緒。|  
|[解除鎖定](../Topic/CComAutoThreadModule::Unlock.md)|會減量鎖定計數在模組和目前執行緒。|  
  
### 資料成員  
  
### 資料成員  
  
|||  
|-|-|  
|[dwThreadID](../Topic/CComAutoThreadModule::dwThreadID.md)|包含目前執行緒的識別項。|  
|[m\_Allocator](../Topic/CComAutoThreadModule::m_Allocator.md)|管理執行緒的選取範圍。|  
|[m\_nThreads](../Topic/CComAutoThreadModule::m_nThreads.md)|包含模組的執行緒數目。|  
|[m\_pApartments](../Topic/CComAutoThreadModule::m_pApartments.md)|處理序模組的 Apartment。|  
  
## 備註  
  
> [!NOTE]
>  這個類別已過時，並取代為 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)[CAtlModule](../../atl/reference/catlmodule-class.md) 衍生類別。  隨後的資訊時機與 ATL 舊版的。  
  
 `CComAutoThreadModule` 從 [CComModule](../../atl/reference/ccommodule-class.md) 衍生自實作 EXE 和 Windows 服務的一個執行緒共用， Apartment Model COM 伺服器。  `CComAutoThreadModule` 使用 [CComApartment](../../atl/reference/ccomapartment-class.md) 處理每個執行緒的單一執行緒 Apartment 中模組。  
  
 例如，當您想要建立在多個 Apartment 的物件時，從 `CComAutoThreadModule` 衍生您的模組。  您可以在您的物件類別定義必須包含 [DECLARE\_CLASSFACTORY\_AUTO\_THREAD](../Topic/DECLARE_CLASSFACTORY_AUTO_THREAD.md) 巨集指定 [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) 做為 Class Factory。  
  
 根據預設， ATL COM AppWizard \(Visual Studio .NET\) 的 ATL 專案精靈會從 `CComModule`衍生您自己的模組。  若要使用 `CComAutoThreadModule`，修改類別定義。  例如：  
  
 [!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/CPP/ccomautothreadmodule-class_1.cpp)]  
  
## 繼承階層架構  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `IAtlAutoThreadModule`  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)  
  
 [CComModule](../../atl/reference/ccommodule-class.md)  
  
 `CComAutoThreadModule`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)
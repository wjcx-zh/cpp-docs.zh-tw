---
title: "CAtlModule Class | Microsoft Docs"
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
  - "ATL::CAtlModule"
  - "CAtlModule"
  - "ATL.CAtlModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAtlModule class"
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAtlModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會提供數個 ATL 模組類別的方法。  
  
## 語法  
  
```  
  
   class ATL_NO_VTABLE CAtlModule :  
public _ATL_MODULE  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CAtlModule::CAtlModule](../Topic/CAtlModule::CAtlModule.md)|建構函式。|  
|[CAtlModule::~CAtlModule](../Topic/CAtlModule::~CAtlModule.md)|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CAtlModule::AddCommonRGSReplacements](../Topic/CAtlModule::AddCommonRGSReplacements.md)|覆寫這個方法會將參數加入至 ATL 註冊元件 \(系統管理員\) 取代對應。|  
|[CAtlModule::AddTermFunc](../Topic/CAtlModule::AddTermFunc.md)|在模組結束時，會將名為的新函式。|  
|[CAtlModule::GetGITPtr](../Topic/CAtlModule::GetGITPtr.md)|傳回全域介面指標。|  
|[CAtlModule::GetLockCount](../Topic/CAtlModule::GetLockCount.md)|傳回鎖定計數。|  
|[CAtlModule::Lock](../Topic/CAtlModule::Lock.md)|將鎖定計數。|  
|[CAtlModule::Term](../Topic/CAtlModule::Term.md)|釋放所有資料成員。|  
|[CAtlModule::Unlock](../Topic/CAtlModule::Unlock.md)|減量鎖定計數。|  
|[CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md)|在指定的資源中的指令碼來註冊或移除註冊物件。|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](../Topic/CAtlModule::UpdateRegistryFromResourceDHelper.md)|這個方法是由 `UpdateRegistryFromResourceD` 呼叫執行登錄更新。|  
|[CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md)|在指定的資源中的指令碼來註冊或移除註冊物件。  這個方法以 ATL 註冊元件靜態連結。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CAtlModule::m\_libid](../Topic/CAtlModule::m_libid.md)|包含目前模組的 GUID。|  
|[CAtlModule::m\_pGIT](../Topic/CAtlModule::m_pGIT.md)|全域清單的介面指標。|  
  
## 備註  
 [CAtlDllModuleT 類別](../../atl/reference/catldllmodulet-class.md)、 [CAtlExeModuleT 類別](../../atl/reference/catlexemodulet-class.md)和 [CAtlServiceModuleT 類別](../../atl/reference/catlservicemodulet-class.md) 會使用這個類別會提供應用程式 DLL、EXE 應用程式和 Windows 服務的支援，名稱分別為、和。  
  
 如需在 ATL 模組的詳細資訊，請參閱 [ATL 模組類別](../../atl/atl-module-classes.md)。  
  
 這個類別會取代用於 ATL 舊版的過時 [CComModule 類別](../../atl/reference/ccommodule-class.md) 。  
  
## 繼承階層架構  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 `CAtlModule`  
  
## 需求  
 **Header:** atlbase.h  
  
## 請參閱  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [模組類別](../../atl/atl-module-classes.md)   
 [登錄元件 \(登錄器\)](../../atl/atl-registry-component-registrar.md)
---
title: "CComModule Class | Microsoft Docs"
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
  - "CComModule"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComModule class"
  - "DLL modules [C++], ATL"
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
caps.latest.revision: 23
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComModule Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

來自 ATL 7.0， `CComModule` 已被取代:如需的詳細資訊請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 。  
  
> [!IMPORTANT]
>  這個類別和其成員不能用於 Windows 執行階段執行的應用程式。  
  
## 語法  
  
```  
class CComModule : public _ATL_MODULE  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComModule::GetClassObject](../Topic/CComModule::GetClassObject.md)|建立指定的 CLSID 的物件。  僅適用於 DLLs。|  
|[CComModule::GetModuleInstance](../Topic/CComModule::GetModuleInstance.md)|傳回 `m_hInst`。|  
|[CComModule::GetResourceInstance](../Topic/CComModule::GetResourceInstance.md)|傳回 `m_hInstResource`。|  
|[CComModule::GetTypeLibInstance](../Topic/CComModule::GetTypeLibInstance.md)|傳回 `m_hInstTypeLib`。|  
|[CComModule::Init](../Topic/CComModule::Init.md)|初始化資料成員。|  
|[CComModule::RegisterClassHelper](../Topic/CComModule::RegisterClassHelper.md)|輸入系統中登錄的物件的標準類別註冊。|  
|[CComModule::RegisterClassObjects](../Topic/CComModule::RegisterClassObjects.md)|註冊類別物件。  僅限 EXE。|  
|[CComModule::RegisterServer](../Topic/CComModule::RegisterServer.md)|更新每個物件的系統登錄物件中對應。|  
|[CComModule::RegisterTypeLib](../Topic/CComModule::RegisterTypeLib.md)|註冊型別程式庫。|  
|[CComModule::RevokeClassObjects](../Topic/CComModule::RevokeClassObjects.md)|移除類別物件。  僅限 EXE。|  
|[CComModule::Term](../Topic/CComModule::Term.md)|釋放資料成員。|  
|[CComModule::UnregisterClassHelper](../Topic/CComModule::UnregisterClassHelper.md)|從系統移除註冊物件的標準類別註冊。|  
|[CComModule::UnregisterServer](../Topic/CComModule::UnregisterServer.md)|移除物件中對應的每個物件。|  
|[CComModule::UpdateRegistryClass](../Topic/CComModule::UpdateRegistryClass.md)|註冊或移除註冊物件的標準類別註冊。|  
|[CComModule::UpdateRegistryFromResourceD](../Topic/CComModule::UpdateRegistryFromResourceD.md)|在指定的資源中的指令碼來註冊或移除註冊物件。|  
|[CComModule::UpdateRegistryFromResourceS](../Topic/CComModule::UpdateRegistryFromResourceS.md)|使用 ATL 註冊元件靜態連結。  在指定的資源中的指令碼來註冊或移除註冊物件。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CComModule::m\_csObjMap](../Topic/CComModule::m_csObjMap.md)|ensures 同步處理對物件的對應資訊。|  
|[CComModule::m\_csTypeInfoHolder](../Topic/CComModule::m_csTypeInfoHolder.md)|ensures 同步至型別程式庫資訊的存取。|  
|[CComModule::m\_csWindowCreate](../Topic/CComModule::m_csWindowCreate.md)|ensures 同步至  視窗在視窗建立時和靜態資料之存取權的類別資訊。|  
|[CComModule::m\_hInst](../Topic/CComModule::m_hInst.md)|包含控制代碼和模組的執行個體。|  
|[CComModule::m\_hInstResource](../Topic/CComModule::m_hInstResource.md)|根據預設，包含控制代碼和模組的執行個體。|  
|[CComModule::m\_hInstTypeLib](../Topic/CComModule::m_hInstTypeLib.md)|根據預設，包含控制代碼和模組的執行個體。|  
|[CComModule::m\_pObjMap](../Topic/CComModule::m_pObjMap.md)|物件的點會維護依模組的執行個體。|  
  
## 備註  
  
> [!NOTE]
>  這個類別已被取代，，和 ATL 程式碼精靈現在使用 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) 和 [CAtlModule](../../atl/reference/catlmodule-class.md) 衍生類別。  請參閱 [ATL 模組類別](../../atl/atl-module-classes.md) 以取得詳細資訊。  遵循中之適用於應用程式的建立 ATL 較舊的版本。  `CComModule` 反向仍為 ATL 的部分功能。  
  
 `CComModule` 實作 COM 伺服器模組，允許用戶端存取模組的元件。  `CComModule` 支援 DLL 和 EXE\) \(處理序 \(本機\) 模組。  
  
 `CComModule` 執行個體使用物件對應維護一組類別的物件定義。  這個物件對應會實作為一部分 `_ATL_OBJMAP_ENTRY` 架構，而且包含資訊:  
  
-   輸入和移除系統中登錄的物件描述。  
  
-   具現化的物件會傳遞 Class Factory。  
  
-   建立用戶端和根物件之間的通訊是元件。  
  
-   實作類別的物件存留期 \(Lifetime\) 管理。  
  
 當您執行 ATL COM AppWizard 時，精靈會自動產生 `_Module`、 `CComModule` 的全域執行個體或從它衍生的類別。  如需 ATL 專案精靈的詳細資訊，請參閱本文 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)。  
  
 除了之外， `CComModule`ATL 提供 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)，實作 EXE 和 Windows 服務的 Apartment Model 模組。  例如，當您想要建立在多個 Apartment 的物件時，從 `CComAutoThreadModule` 衍生您的模組。  
  
## 繼承階層架構  
 [\_ATL\_MODULE](../Topic/_ATL_MODULE.md)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CComModule`  
  
## 需求  
 `Header:` atlbase.h  
  
## 請參閱  
 [Class Overview](../../atl/atl-class-overview.md)
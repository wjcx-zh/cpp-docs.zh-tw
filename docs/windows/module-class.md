---
title: "Module 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Module 類別"
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示相關物件的集合。  
  
## 語法  
  
```  
  
template<  
   ModuleType moduleType  
>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
#### 參數  
 `moduleType`  
 一或多個 [RuntimeClassType](../windows/moduletype-enumeration.md) 列舉值的組合。  
  
## Members  
  
### 受保護的類別  
  
|名稱|描述|  
|--------|--------|  
|[Module::GenericReleaseNotifier 類別](../windows/module-genericreleasenotifier-class.md)|目前模組中最後一個物件被釋放時叫用事件處理常式。  事件處理常式由 Lambda、functor、或 pointer\-to\-function 指定。|  
|[Module::MethodReleaseNotifier 類別](../windows/module-methodreleasenotifier-class.md)|目前模組中最後一個物件被釋放時叫用事件處理常式。  事件處理常式由物件及其指標方法成員指定。|  
|[Module::ReleaseNotifier 類別](../windows/module-releasenotifier-class.md)|模組中最後一個物件釋放時會叫用一個事件處理常式。|  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Module::~Module 解構函式](../windows/module-tilde-module-destructor.md)|取消初始化模組類別目前的執行個體。|  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[Module::Module 建構函式](../windows/module-module-constructor.md)|初始化 Module 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[Module::Create 方法](../windows/module-create-method.md)|建立模組的執行個體。|  
|[Module::DecrementObjectCount 方法](../windows/module-decrementobjectcount-method.md)|遞減模組追蹤的物件數目。|  
|[Module::GetActivationFactory 方法](../windows/module-getactivationfactory-method.md)|取得模組的啟動 Factory。|  
|[Module::GetClassObject 方法](../windows/module-getclassobject-method.md)|擷取類別 Factory 的快取。|  
|[Module::GetModule 方法](../windows/module-getmodule-method.md)|建立模組的執行個體。|  
|[Module::GetObjectCount 方法](../windows/module-getobjectcount-method.md)|擷取這個模組所處理的物件數目。|  
|[Module::IncrementObjectCount 方法](../windows/module-incrementobjectcount-method.md)|遞增將模組追蹤的物件數目。|  
|[Module::RegisterCOMObject 方法](../windows/module-registercomobject-method.md)|註冊一或多個 COM 物件，讓其他應用程式可以連接至這些項目。|  
|[Module::RegisterObjects 方法](../windows/module-registerobjects-method.md)|COM 註冊器或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件，讓其他應用程式可以連接至這些項目。|  
|[Module::RegisterWinRTObject 方法](../windows/module-registerwinrtobject-method.md)|註冊一或多個 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件，讓其他應用程式可以連接至這些項目。|  
|[Module::Terminate 方法](../windows/module-terminate-method.md)|讓產生模組具現化的任何 Factory 關閉。|  
|[Module::UnregisterCOMObject 方法](../windows/module-unregistercomobject-method.md)|解除登錄一或多個 COM 物件，以防止其他應用程式與它們連接。|  
|[Module::UnregisterObjects 方法](../windows/module-unregisterobjects-method.md)|解除登錄在指定之模組的物件，讓其他應用程式無法連接到它們。|  
|[Module::UnregisterWinRTObject 方法](../windows/module-unregisterwinrtobject-method.md)|解除註冊一或多個 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 物件，讓其他應用程式無法連接到它們。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[Module::Create 方法](../windows/module-create-method.md)|建立模組的執行個體。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[Module::objectCount\_ 資料成員](../windows/module-objectcount-data-member.md)|記錄多少類別是以 [認可](../windows/make-function.md) 函式建立的。|  
|[Module::releaseNotifier\_ 資料成員](../windows/module-releasenotifier-data-member.md)|保留一個指向 ReleaseNotifier 物件的指標。|  
  
### 巨集  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|填入包含一個 Factory 可以建立指定的類別執行個體的內部快取。  這個巨集指定預設 Factory 和群組 ID 參數。|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|填入包含一個 Factory 可以建立指定的類別執行個體的內部快取。  這個巨集可讓您指定特定 Factory 參數。|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|填入包含一個 Factory 可以建立指定的類別執行個體的內部快取。  這個巨集可讓您指定特定 Factory 和群組 ID 參數。|  
  
## 繼承階層架構  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)
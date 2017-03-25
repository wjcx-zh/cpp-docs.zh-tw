---
title: "IResourceManager 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 2d054bd632db90708d90fe8d791965b47f713493
ms.lasthandoff: 03/17/2017

---
# <a name="iresourcemanager-structure"></a>IResourceManager 結構
並行執行階段資源管理員的介面。 這是排程器用來與資源管理員通訊的介面。  
  
## <a name="syntax"></a>語法  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-enumerations"></a>公用列舉類型  
  
|名稱|說明|  
|----------|-----------------|  
|[Iresourcemanager:: Osversion](#osversion)|代表作業系統版本的列舉類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Iresourcemanager:: Createnodetopology](#createnodetopology)|現在只在偵錯組建的執行階段，這個方法是設計來幫助您測試在不同硬體拓撲，而不需要實際的硬體組態的比對的資源管理員測試攔截程序。 使用執行階段的零售版本，這個方法會傳回而不執行任何動作。|  
|[Iresourcemanager:: Getavailablenodecount](#getavailablenodecount)|傳回可供資源管理員使用的節點數目。|  
|[Iresourcemanager:: Getfirstnode](#getfirstnode)|傳回資源管理員所定義之列舉順序中的第一個節點。|  
|[Iresourcemanager:: Reference](#reference)|資源管理員執行個體上的參考計數遞增。|  
|[Iresourcemanager:: Registerscheduler](#registerscheduler)|註冊排程器與資源管理員。 排程器註冊後，它應該與資源管理員使用`ISchedulerProxy`傳回的介面。|  
|[Iresourcemanager:: Release](#release)|遞減參考計數的資源管理員執行個體。 資源管理員會終結其參考計數歸`0`。|  
  
## <a name="remarks"></a>備註  
 使用[CreateResourceManager](concurrency-namespace-functions.md)函數來取得單一資源管理員執行個體的介面。 方法遞增參考計數在資源管理員，並且應該叫用[iresourcemanager:: Release](#release)方法，以釋放參考，當您在使用資源管理員。 一般而言，您建立每個排程器將在建立時，叫用這個方法並關機後釋放參考至資源管理員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IResourceManager`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="createnodetopology"></a>Iresourcemanager:: Createnodetopology 方法  
 現在只在偵錯組建的執行階段，這個方法是設計來幫助您測試在不同硬體拓撲，而不需要實際的硬體組態的比對的資源管理員測試攔截程序。 使用執行階段的零售版本，這個方法會傳回而不執行任何動作。  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>參數  
 `nodeCount`  
 模擬的處理器節點數目。  
  
 `pCoreCount`  
 陣列，指定每個節點上的核心數目。  
  
 `pNodeDistance`  
 指定節點之間的距離兩個節點的矩陣。 這個參數的值可以`NULL`。  
  
 `pProcessorGroups`  
 每個節點所屬的陣列，指定處理器群組。  
  
### <a name="remarks"></a>備註  
 [invalid_argument](../../../standard-library/invalid-argument-class.md)便會擲回參數`nodeCount`值`0`傳入，或如果參數`pCoreCount`值`NULL`。  
  
 [invalid_operation](invalid-operation-class.md)程序中的其他排程器存在時，會呼叫這個方法會擲回。  
  
##  <a name="getavailablenodecount"></a>Iresourcemanager:: Getavailablenodecount 方法  
 傳回可供資源管理員使用的節點數目。  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 使用資源管理員的節點數目。  
  
##  <a name="getfirstnode"></a>Iresourcemanager:: Getfirstnode 方法  
 傳回資源管理員所定義之列舉順序中的第一個節點。  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 資源管理員所定義的列舉順序中第一個節點。  
  
##  <a name="iresourcemanager__osversion"></a>Iresourcemanager:: Osversion 列舉  
 代表作業系統版本的列舉類型。  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>Iresourcemanager:: Reference 方法  
 資源管理員執行個體上的參考計數遞增。  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 產生的參考計數。  
  
##  <a name="registerscheduler"></a>Iresourcemanager:: Registerscheduler 方法  
 註冊排程器與資源管理員。 排程器註冊後，它應該與資源管理員使用`ISchedulerProxy`傳回的介面。  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>參數  
 `pScheduler`  
 `IScheduler`註冊排程器的介面。  
  
 `version`  
 排程器進行通訊與資源管理員使用的通訊介面版本。 使用版本可讓資源管理員，同時允許排程器，取得存取權給較舊功能發展通訊介面。 要使用 Visual Studio 2010 中的資源管理員功能的排程器應該使用版本`CONCRT_RM_VERSION_1`。  
  
### <a name="return-value"></a>傳回值  
 `ISchedulerProxy`資源管理員與您的排程器相關聯的介面。 您的排程器應該使用此介面上，從這個點通訊與資源管理員。  
  
### <a name="remarks"></a>備註  
 使用此方法以初始化與資源管理員的通訊。 此方法將`IScheduler`與排程器介面`ISchedulerProxy`介面並回到您的實際操作。 要求執行資源以供您的排程器，或訂閱執行緒與資源管理員，您可以使用傳回的介面。 資源管理員會使用所傳回的排程器原則的原則項目[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法來判斷何種執行緒排程器將需要執行工作。 如果您`SchedulerKind`原則機碼具有值`UmsThreadDefault`值回讀出做為值的原則和`UmsThreadDefault`、`IScheduler`傳遞給方法的介面必須`IUMSScheduler`介面。  
  
 方法會擲回`invalid_argument`例外狀況如果參數`pScheduler`值`NULL`或參數`version`不是有效的版本，通訊介面。  
  
##  <a name="release"></a>Iresourcemanager:: Release 方法  
 遞減參考計數的資源管理員執行個體。 資源管理員會終結其參考計數歸`0`。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 產生的參考計數。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ISchedulerProxy 結構](ischedulerproxy-structure.md)   
 [IScheduler 結構](ischeduler-structure.md)


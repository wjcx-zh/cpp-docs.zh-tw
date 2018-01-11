---
title: "IResourceManager 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0a88cfafe9bbfdc04776050a0a956bf9a8b6766e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iresourcemanager-structure"></a>IResourceManager 結構
並行執行階段資源管理員的介面。 這是排程器用來與資源管理員通訊的介面。  
  
## <a name="syntax"></a>語法  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-enumerations"></a>公用列舉類型  
  
|名稱|描述|  
|----------|-----------------|  
|[Iresourcemanager:: Osversion](#osversion)|代表作業系統版本的列舉類型。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Iresourcemanager:: Createnodetopology](#createnodetopology)|目前只在偵錯組建的執行階段，這個方法是設計來加速測試資源管理員的各種硬體拓撲，而不需要實際的硬體符合組態上測試勾點。 執行階段的零售版本，這個方法會傳回而不執行任何動作。|  
|[Iresourcemanager:: Getavailablenodecount](#getavailablenodecount)|傳回可供資源管理員使用的節點數目。|  
|[Iresourcemanager:: Getfirstnode](#getfirstnode)|傳回資源管理員所定義之列舉順序中的第一個節點。|  
|[Iresourcemanager:: Reference](#reference)|資源管理員執行個體上的參考計數遞增。|  
|[Iresourcemanager:: Registerscheduler](#registerscheduler)|註冊排程器與資源管理員。 排程器註冊後，它應該與資源管理員使用`ISchedulerProxy`傳回的介面。|  
|[Iresourcemanager:: Release](#release)|資源管理員執行個體的參考計數遞減。 資源管理員會終結其參考計數變成`0`。|  
  
## <a name="remarks"></a>備註  
 使用[CreateResourceManager](concurrency-namespace-functions.md)函數來取得單一資源管理員執行個體的介面。 方法遞增參考計數在資源管理員，並且應該叫用[iresourcemanager:: Release](#release)方法，以釋放參考，當您完成使用資源管理員。 一般而言，您所建立的每個排程器會叫用這個方法在建立期間，並關機後釋放資源管理員的參考。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IResourceManager`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="createnodetopology"></a>Iresourcemanager:: Createnodetopology 方法  
 目前只在偵錯組建的執行階段，這個方法是設計來加速測試資源管理員的各種硬體拓撲，而不需要實際的硬體符合組態上測試勾點。 執行階段的零售版本，這個方法會傳回而不執行任何動作。  
  
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
 指定節點之間的距離兩個節點的矩陣。 這個參數可以具有值`NULL`。  
  
 `pProcessorGroups`  
 每個節點所屬的陣列，指定處理器群組。  
  
### <a name="remarks"></a>備註  
 [invalid_argument](../../../standard-library/invalid-argument-class.md)則會擲回參數`nodeCount`值`0`傳入，或如果參數`pCoreCount`值`NULL`。  
  
 [invalid_operation](invalid-operation-class.md)如果處理序中的其他排程器存在時，會呼叫這個方法會擲回。  
  
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
 資源管理員所定義的列舉順序中的第一個節點。  
  
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
 排程器進行通訊與資源管理員使用的通訊介面版本。 使用版本可讓資源管理員，同時允許排程器，以取得存取權的舊版功能發展的通訊介面。 要使用 Visual Studio 2010 中的資源管理員功能的排程器應該使用版本`CONCRT_RM_VERSION_1`。  
  
### <a name="return-value"></a>傳回值  
 `ISchedulerProxy`資源管理員與您的排程器相關聯的介面。 您的排程器應該使用此介面上，從這個點通訊與資源管理員。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法會起始與資源管理員的通訊。 此方法將`IScheduler`與排程器的介面`ISchedulerProxy`介面，並回到您的手。 要求執行資源以供您的排程器，或訂閱執行緒與資源管理員，您可以使用傳回的介面。 資源管理員會使用從所傳回的排程器原則的原則元素[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法來判斷何種執行緒排程器需要執行工作。 如果您`SchedulerKind`原則機碼具有值`UmsThreadDefault`和值唯讀的值與原則從傳回`UmsThreadDefault`、`IScheduler`傳遞給方法的介面必須`IUMSScheduler`介面。  
  
 方法會擲回`invalid_argument`例外狀況如果參數`pScheduler`值`NULL`或參數`version`不是有效的版本的通訊介面。  
  
##  <a name="release"></a>Iresourcemanager:: Release 方法  
 資源管理員執行個體的參考計數遞減。 資源管理員會終結其參考計數變成`0`。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>傳回值  
 產生的參考計數。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ISchedulerProxy 結構](ischedulerproxy-structure.md)   
 [IScheduler 結構](ischeduler-structure.md)

---
title: IResourceManager 結構
ms.date: 11/04/2016
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
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 7c6ed48c8896b54faa8418719f0ab7c7fa1df7c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657189"
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
|[IResourceManager::OSVersion](#osversion)|代表作業系統版本的列舉類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|目前只在偵錯組建的執行階段，這個方法是為了協助測試在不同硬體拓撲，而不需要實際的硬體符合組態的 Resource Manager 而設計的測試勾點。 執行階段的零售版本，這個方法會傳回而不執行任何動作。|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|傳回可供資源管理員使用的節點數目。|
|[IResourceManager::GetFirstNode](#getfirstnode)|傳回資源管理員所定義之列舉順序中的第一個節點。|
|[IResourceManager::Reference](#reference)|Resource Manager 執行個體上的參考計數會遞增。|
|[IResourceManager::RegisterScheduler](#registerscheduler)|使用 Resource Manager 註冊排程器。 一旦註冊排程器，它應該與 Resource Manager 使用`ISchedulerProxy`傳回的介面。|
|[IResourceManager::Release](#release)|遞減參考計數的 Resource Manager 執行個體。 Resource Manager 會終結其參考計數歸`0`。|

## <a name="remarks"></a>備註

使用[CreateResourceManager](concurrency-namespace-functions.md)函式來取得單一 Resource Manager 執行個體的介面。 方法會遞增參考計數在 Resource Manager 中，並應叫用[iresourcemanager:: Release](#release)釋放參考，當您完成使用 Resource Manager 時的方法。 一般而言，您所建立的每個排程器會叫用這個方法，在建立期間，並釋放至 Resource Manager 中的參考之後會關閉。

## <a name="inheritance-hierarchy"></a>繼承階層

`IResourceManager`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="createnodetopology"></a>  Iresourcemanager:: Createnodetopology 方法

目前只在偵錯組建的執行階段，這個方法是為了協助測試在不同硬體拓撲，而不需要實際的硬體符合組態的 Resource Manager 而設計的測試勾點。 執行階段的零售版本，這個方法會傳回而不執行任何動作。

```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>參數

*nodeCount*<br/>
要模擬的處理器節點數目。

*pCoreCount*<br/>
陣列，指定每個節點上的核心數目。

*pNodeDistance*<br/>
指定節點之間的距離兩個節點的矩陣。 此參數的值`NULL`。

*pProcessorGroups*<br/>
每個節點所屬的陣列，指定處理器群組。

### <a name="remarks"></a>備註

[invalid_argument](../../../standard-library/invalid-argument-class.md)便會擲回參數`nodeCount`具有值`0`傳入，或如果參數`pCoreCount`的值`NULL`。

[invalid_operation](invalid-operation-class.md)如果其他排程器存在於處理程序時，會呼叫這個方法會擲回。

##  <a name="getavailablenodecount"></a>  Iresourcemanager:: Getavailablenodecount 方法

傳回可供資源管理員使用的節點數目。

```
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>傳回值

至 Resource Manager 中可用的節點數目。

##  <a name="getfirstnode"></a>  Iresourcemanager:: Getfirstnode 方法

傳回資源管理員所定義之列舉順序中的第一個節點。

```
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>傳回值

在資源管理員所定義的列舉順序中的第一個節點。

##  <a name="iresourcemanager__osversion"></a>  Iresourcemanager:: Osversion 列舉

代表作業系統版本的列舉類型。

```
enum OSVersion;
```

##  <a name="reference"></a>  Iresourcemanager:: Reference 方法

Resource Manager 執行個體上的參考計數會遞增。

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>傳回值

產生的參考計數。

##  <a name="registerscheduler"></a>  Iresourcemanager:: Registerscheduler 方法

使用 Resource Manager 註冊排程器。 一旦註冊排程器，它應該與 Resource Manager 使用`ISchedulerProxy`傳回的介面。

```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>參數

*pScheduler*<br/>
`IScheduler`註冊排程器的介面。

*version*<br/>
排程器通訊使用 Resource Manager 中使用的通訊介面版本。 使用版本可讓 Resource Manager，同時允許排程器，以取得存取權給較舊的功能改進的通訊介面。 想要使用 Visual Studio 2010 中的 Resource Manager 功能的排程器應該使用版本`CONCRT_RM_VERSION_1`。

### <a name="return-value"></a>傳回值

`ISchedulerProxy` Resource Manager 與您的排程器相關聯的介面。 您的排程器應使用此介面上，從這裡開始通訊使用 Resource Manager。

### <a name="remarks"></a>備註

使用這個方法，以起始使用 Resource Manager 中的通訊。 方法產生關聯`IScheduler`介面與排程器`ISchedulerProxy`介面和回到您的手。 若要要求執行資源以供您的排程器，或訂閱執行緒使用 Resource Manager 中，您可以使用傳回的介面。 Resource Manager 會使用所傳回的排程器原則的原則項目[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法，以判斷哪種類型的執行緒排程器需要執行工作。 如果您`SchedulerKind`原則索引鍵具有值`UmsThreadDefault`並從傳回的值與原則讀取值`UmsThreadDefault`，則`IScheduler`傳遞給方法的介面必須`IUMSScheduler`介面。

方法會擲回`invalid_argument`例外狀況如果參數`pScheduler`具有值`NULL`或者參數`version`不是有效的版本，通訊介面。

##  <a name="release"></a>  Iresourcemanager:: Release 方法

遞減參考計數的 Resource Manager 執行個體。 Resource Manager 會終結其參考計數歸`0`。

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

產生的參考計數。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISchedulerProxy 結構](ischedulerproxy-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)

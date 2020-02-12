---
title: IResourceManager 結構
ms.date: 03/27/2019
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
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142976"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 結構

並行執行階段資源管理員的介面。 這是排程器用來與資源管理員通訊的介面。

## <a name="syntax"></a>語法

```cpp
struct IResourceManager;
```

## <a name="members"></a>成員

### <a name="public-enumerations"></a>公用列舉型別

|名稱|描述|
|----------|-----------------|
|[IResourceManager：： OSVersion](#osversion)|代表作業系統版本的列舉類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IResourceManager：： CreateNodeTopology](#createnodetopology)|此方法僅存在於執行時間的 debug 組建中，這是一種測試攔截，其設計目的是為了協助測試不同硬體拓撲的 Resource Manager，而不需要實際符合設定的硬體。 在執行時間的零售組建中，這個方法會傳回，而不會執行任何動作。|
|[IResourceManager：： GetAvailableNodeCount](#getavailablenodecount)|傳回可供資源管理員使用的節點數目。|
|[IResourceManager：： GetFirstNode](#getfirstnode)|傳回資源管理員所定義之列舉順序中的第一個節點。|
|[IResourceManager：： Reference](#reference)|遞增 Resource Manager 實例上的參考計數。|
|[IResourceManager：： RegisterScheduler](#registerscheduler)|向 Resource Manager 註冊排程器。 一旦註冊排程器，就應該使用傳回的 `ISchedulerProxy` 介面與 Resource Manager 進行通訊。|
|[IResourceManager：： Release](#release)|遞減 Resource Manager 實例上的參考計數。 Resource Manager 會在其參考計數進入 `0`時終結。|

## <a name="remarks"></a>備註

使用[CreateResourceManager](concurrency-namespace-functions.md)函數來取得單一 Resource Manager 實例的介面。 方法會遞增 Resource Manager 上的參考計數，而且您應該在完成 Resource Manager 時，叫用[IResourceManager：： release](#release)方法以釋放參考。 一般來說，您建立的每個排程器都會在建立期間叫用這個方法，並在關閉後釋放 Resource Manager 的參考。

## <a name="inheritance-hierarchy"></a>繼承階層

`IResourceManager`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="createnodetopology"></a>IResourceManager：： CreateNodeTopology 方法

此方法僅存在於執行時間的 debug 組建中，這是一種測試攔截，其設計目的是為了協助測試不同硬體拓撲的 Resource Manager，而不需要實際符合設定的硬體。 在執行時間的零售組建中，這個方法會傳回，而不會執行任何動作。

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>參數

*nodeCount*<br/>
模擬的處理器節點數目。

*pCoreCount*<br/>
陣列，指定每個節點上的核心數目。

*pNodeDistance*<br/>
指定兩個節點之間的節點距離的矩陣。 這個參數的值可以 `NULL`。

*pProcessorGroups*<br/>
陣列，指定每個節點所屬的處理器群組。

### <a name="remarks"></a>備註

如果參數 `nodeCount` 已傳入值 `0`，或參數 `pCoreCount` 的值為 `NULL`，則會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md) 。

如果在處理常式中有其他排程器時呼叫這個方法，則會擲回[invalid_operation](invalid-operation-class.md) 。

## <a name="getavailablenodecount"></a>IResourceManager：： GetAvailableNodeCount 方法

傳回可供資源管理員使用的節點數目。

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>傳回值

可供 Resource Manager 使用的節點數目。

## <a name="getfirstnode"></a>IResourceManager：： GetFirstNode 方法

傳回資源管理員所定義之列舉順序中的第一個節點。

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>傳回值

列舉順序中的第一個節點，如 Resource Manager 所定義。

## <a name="osversion"></a>IResourceManager：： OSVersion 列舉

代表作業系統版本的列舉類型。

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager：： Reference 方法

遞增 Resource Manager 實例上的參考計數。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>傳回值

產生的參考計數。

## <a name="registerscheduler"></a>IResourceManager：： RegisterScheduler 方法

向 Resource Manager 註冊排程器。 一旦註冊排程器，就應該使用傳回的 `ISchedulerProxy` 介面與 Resource Manager 進行通訊。

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>參數

*pScheduler*<br/>
要註冊之排程器的 `IScheduler` 介面。

*version*<br/>
排程器用來與 Resource Manager 通訊的通訊介面版本。 使用版本可讓 Resource Manager 發展通訊介面，同時允許排程器取得舊版功能的存取權。 想要使用 Visual Studio 2010 中 Resource Manager 功能的排程器應該使用版本 `CONCRT_RM_VERSION_1`。

### <a name="return-value"></a>傳回值

Resource Manager 與您的排程器相關聯的 `ISchedulerProxy` 介面。 您的排程器應該使用此介面，從上的這個點與 Resource Manager 進行通訊。

### <a name="remarks"></a>備註

使用此方法來起始與 Resource Manager 的通訊。 方法會將排程器的 `IScheduler` 介面與 `ISchedulerProxy` 介面建立關聯，並將其交給您。 您可以使用傳回的介面來要求執行資源供排程器使用，或用來訂閱具有 Resource Manager 的執行緒。 Resource Manager 會使用[IScheduler：： GetPolicy](ischeduler-structure.md#getpolicy)方法所傳回的排程器原則中的原則元素，來判斷排程器執行工作所需的執行緒類型。 如果您的 `SchedulerKind` 原則金鑰具有 `UmsThreadDefault` 值，而且值是從原則中讀回值 `UmsThreadDefault`，則傳遞至方法的 `IScheduler` 介面必須是 `IUMSScheduler` 介面。

如果參數 `pScheduler` 的值 `NULL`，或如果參數 `version` 不是有效的通訊介面版本，方法會擲回 `invalid_argument` 例外狀況。

## <a name="release"></a>IResourceManager：： Release 方法

遞減 Resource Manager 實例上的參考計數。 Resource Manager 會在其參考計數進入 `0`時終結。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

產生的參考計數。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISchedulerProxy 結構](ischedulerproxy-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)

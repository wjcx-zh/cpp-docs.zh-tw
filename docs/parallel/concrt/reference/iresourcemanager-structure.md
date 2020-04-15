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
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368180"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 結構

並行執行階段資源管理員的介面。 這是排程器用來與資源管理員通訊的介面。

## <a name="syntax"></a>語法

```cpp
struct IResourceManager;
```

## <a name="members"></a>成員

### <a name="public-enumerations"></a>公用列舉類型

|名稱|描述|
|----------|-----------------|
|[I 資源管理員:OSVersion](#osversion)|代表作業系統版本的列舉類型。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I 資源管理員::建立節點拓撲](#createnodetopology)|此方法僅在運行時的調試版本中存在,它是一個測試挂鉤,旨在方便在不同硬體拓撲上測試資源管理器,而無需實際硬體匹配配置。 使用運行時的零售生成時,此方法將返回而不執行任何操作。|
|[I 資源管理員::取得可用節點計數](#getavailablenodecount)|傳回可供資源管理員使用的節點數目。|
|[I 資源管理員::取得第一節點](#getfirstnode)|傳回資源管理員所定義之列舉順序中的第一個節點。|
|[I資源管理員:參考](#reference)|增加資源管理員實例上的引用計數。|
|[I資源管理員::註冊時程表](#registerscheduler)|向資源管理器註冊計劃程式。 註冊計劃程式后,它應使用返回的`ISchedulerProxy`介面與資源管理器通信。|
|[I 資源管理員::發佈](#release)|在資源管理器實例上取消引用計數。 當資源管理員的引用計數轉到`0`時,它將被銷毀。|

## <a name="remarks"></a>備註

使用[CreateResourceManager](concurrency-namespace-functions.md)函數獲取與單一資源管理器實例的介面。 該方法將引用計數遞增到資源管理員上,您應該調用[IResourceManager:::釋放](#release)方法,在使用資源管理器時釋放引用。 通常,您創建的每個計劃程式將在創建期間調用此方法,並在資源管理器關閉后釋放對資源管理員的引用。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`IResourceManager`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>I資源管理員::建立節點拓撲方法

此方法僅在運行時的調試版本中存在,它是一個測試挂鉤,旨在方便在不同硬體拓撲上測試資源管理器,而無需實際硬體匹配配置。 使用運行時的零售生成時,此方法將返回而不執行任何操作。

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>參數

*節點計數*<br/>
正在類比的處理器節點數。

*pCore( S) Count*<br/>
指定每個節點上的內核數的陣列。

*pNode 距離*<br/>
指定任意兩個節點之間的節點距離的矩陣。 這裡可以有值`NULL`。

*p 處理器群組*<br/>
指定每個節點所屬的處理器組的陣列。

### <a name="remarks"></a>備註

如果`nodeCount`參數`0`已傳入值,或者`pCoreCount`參數`NULL`具有值 ,則引發[invalid_argument。](../../../standard-library/invalid-argument-class.md)

如果調用此方法,而進程中存在其他計劃程式,則引發[invalid_operation。](invalid-operation-class.md)

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>I 資源管理員::取得可用節點計數方法

傳回可供資源管理員使用的節點數目。

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>傳回值

資源管理器可用的節點數。

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>I 資源管理員:取得第一節點方法

傳回資源管理員所定義之列舉順序中的第一個節點。

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>傳回值

資源管理員定義的枚舉順序中的第一個節點。

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>I 資源管理員::OSversion 枚舉

代表作業系統版本的列舉類型。

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>I資源管理員:參考方法

增加資源管理員實例上的引用計數。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>傳回值

生成的引用計數。

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>I資源管理員::註冊調度器方法

向資源管理器註冊計劃程式。 註冊計劃程式后,它應使用返回的`ISchedulerProxy`介面與資源管理器通信。

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>參數

*p 時間*<br/>
要`IScheduler`註冊的計劃程式的介面。

*version*<br/>
計劃程式用於與資源管理器通信的通信介面的版本。 使用版本允許資源管理器發展通信介面,同時允許計劃程序訪問較舊的功能。 希望使用 Visual Studio 2010 中存在的資源管理員功能的計畫`CONCRT_RM_VERSION_1`程式應使用版本 。

### <a name="return-value"></a>傳回值

資源管理員`ISchedulerProxy`與您的計劃程序關聯的介面。 此時,您的計劃程式應使用此介面與資源管理器進行通信。

### <a name="remarks"></a>備註

使用此方法啟動與資源管理器的通信。 該方法將計劃程式`IScheduler`的介面與介面關聯`ISchedulerProxy`,並將其交還給您。 您可以使用返回的介面請求執行資源供計畫程式使用,或者與資源管理器訂閱線程。 資源管理員將使用[I-計劃器返回](ischeduler-structure.md#getpolicy)的計畫程式策略的策略元素來確定計畫程式執行工作所需的線程類型。 `SchedulerKind`如果策略`UmsThreadDefault`鍵具有該值,並且該值作為`UmsThreadDefault`值 從策略中讀出,則傳遞`IScheduler`給 方法的介面`IUMSScheduler`必須是介面 。

`invalid_argument`如果參數`pScheduler`具有`NULL`值`version`或參數 不是通信介面的有效版本,則該方法將引發異常。

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>I資源管理員::發佈方法

在資源管理器實例上取消引用計數。 當資源管理員的引用計數轉到`0`時,它將被銷毀。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>傳回值

生成的引用計數。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)<br/>
[ISchedulerProxy 結構](ischedulerproxy-structure.md)<br/>
[IScheduler 結構](ischeduler-structure.md)

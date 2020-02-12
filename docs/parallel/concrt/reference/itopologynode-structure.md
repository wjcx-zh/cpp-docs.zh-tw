---
title: ITopologyNode 結構
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140052"
---
# <a name="itopologynode-structure"></a>ITopologyNode 結構

資源管理員所定義的拓撲節點介面。 節點可包含一個或多個執行資源。

## <a name="syntax"></a>語法

```cpp
struct ITopologyNode;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ITopologyNode：： GetExecutionResourceCount](#getexecutionresourcecount)|傳回結合在這個節點下的執行資源數目。|
|[ITopologyNode：： GetFirstExecutionResource](#getfirstexecutionresource)|傳回依列舉順序在這個節點下設為群組的第一個執行資源。|
|[ITopologyNode：： GetId](#getid)|傳回此節點 Resource Manager 的唯一識別碼。|
|[ITopologyNode：： GetNext](#getnext)|讓介面返回列舉順序中的下一個拓撲節點。|
|[ITopologyNode：： GetNumaNode](#getnumanode)|傳回此資源 Maanger 節點所屬的 Windows 指派的 NUMA 節點編號。|

## <a name="remarks"></a>備註

此介面通常用來逐步引導系統的拓撲，如 Resource Manager 所觀察到的。

## <a name="inheritance-hierarchy"></a>繼承階層

`ITopologyNode`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h。h

**命名空間：** concurrency

## <a name="getexecutionresourcecount"></a>ITopologyNode：： GetExecutionResourceCount 方法

傳回結合在這個節點下的執行資源數目。

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>傳回值

結合在這個節點下的執行資源數目。

## <a name="getfirstexecutionresource"></a>ITopologyNode：： GetFirstExecutionResource 方法

傳回依列舉順序在這個節點下設為群組的第一個執行資源。

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>傳回值

依列舉順序在這個節點下設為群組的第一個執行資源。

## <a name="getid"></a>ITopologyNode：： GetId 方法

傳回此節點 Resource Manager 的唯一識別碼。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

此節點 Resource Manager 的唯一識別碼。

### <a name="remarks"></a>備註

並行執行階段代表處理器節點群組中系統上的硬體執行緒。 節點通常是從系統的硬體拓朴衍生而來。 例如，特定通訊端或特定 NUMA 節點上的所有處理器都可能屬於相同的處理器節點。 Resource Manager 會將唯一識別碼指派給這些節點，從 `0` 到，包括 `nodeCount - 1`，其中 `nodeCount` 代表系統上的處理器節點總數。

您可以從函數[GetProcessorNodeCount](concurrency-namespace-functions.md)取得節點計數。

## <a name="getnext"></a>ITopologyNode：： GetNext 方法

讓介面返回列舉順序中的下一個拓撲節點。

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>傳回值

介面返回列舉順序中的下一個節點。 如果系統拓撲的列舉順序中沒有其他節點，這個方法將傳回值 `NULL`。

## <a name="getnumanode"></a>ITopologyNode：： GetNumaNode 方法

傳回此資源 Maanger 節點所屬的 Windows 指派的 NUMA 節點編號。

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>傳回值

此 Resource Manager 節點所屬的 Windows 指派 NUMA 節點編號。

### <a name="remarks"></a>備註

在屬於此節點的虛擬處理器根上執行的執行緒 proxy，對於此方法所傳回之 NUMA 節點的 NUMA 節點層級，至少會有相似性。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

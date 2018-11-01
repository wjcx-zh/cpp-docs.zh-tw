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
ms.openlocfilehash: 4f880e3c44cd9f301aa65d45500ed7f1d1725bc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636653"
---
# <a name="itopologynode-structure"></a>ITopologyNode 結構

資源管理員所定義的拓撲節點介面。 節點可包含一個或多個執行資源。

## <a name="syntax"></a>語法

```
struct ITopologyNode;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|傳回結合在這個節點下的執行資源數目。|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|傳回依列舉順序在這個節點下設為群組的第一個執行資源。|
|[ITopologyNode::GetId](#getid)|傳回這個節點的 Resource Manager 的唯一識別碼。|
|[ITopologyNode::GetNext](#getnext)|讓介面返回列舉順序中的下一個拓撲節點。|
|[ITopologyNode::GetNumaNode](#getnumanode)|傳回 Windows 指派給這個資源管理員節點所屬的 NUMA 節點數目。|

## <a name="remarks"></a>備註

此介面通常用於為觀察資源管理員逐步系統的拓撲。

## <a name="inheritance-hierarchy"></a>繼承階層

`ITopologyNode`

## <a name="requirements"></a>需求

**標頭：** concrtrm.h

**命名空間：** concurrency

##  <a name="getexecutionresourcecount"></a>  Itopologynode:: Getexecutionresourcecount 方法

傳回結合在這個節點下的執行資源數目。

```
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>傳回值

結合在這個節點下的執行資源數目。

##  <a name="getfirstexecutionresource"></a>  Itopologynode:: Getfirstexecutionresource 方法

傳回依列舉順序在這個節點下設為群組的第一個執行資源。

```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>傳回值

依列舉順序在這個節點下設為群組的第一個執行資源。

##  <a name="getid"></a>  Itopologynode:: Getid 方法

傳回這個節點的 Resource Manager 的唯一識別碼。

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

Resource Manager 的此節點的唯一識別碼。

### <a name="remarks"></a>備註

並行執行階段代表處理器節點群組中的系統上的硬體執行緒數目。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都屬於相同處理器節點。 Resource Manager 會將唯一識別碼指派給這些節點從開始`0`最多且含`nodeCount - 1`，其中`nodeCount`表示系統上的處理器節點總數。

可以從函數中取得的節點計數[GetProcessorNodeCount](concurrency-namespace-functions.md)。

##  <a name="getnext"></a>  Itopologynode:: Getnext 方法

讓介面返回列舉順序中的下一個拓撲節點。

```
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>傳回值

介面返回列舉順序中的下一個節點。 如果系統拓撲的列舉順序中沒有其他節點，這個方法將傳回值 `NULL`。

##  <a name="getnumanode"></a>  Itopologynode:: Getnumanode 方法

傳回 Windows 指派給這個資源管理員節點所屬的 NUMA 節點數目。

```
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>傳回值

Windows 指派給這個資源管理員節點所屬的 NUMA 節點數目。

### <a name="remarks"></a>備註

屬於這個節點的虛擬處理器根上執行的執行緒 proxy 會有同質性至少 NUMA 節點，這個方法所傳回的 NUMA 節點層級。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

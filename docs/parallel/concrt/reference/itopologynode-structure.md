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
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368112"
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
|[I拓撲節點:取得執行資源計數](#getexecutionresourcecount)|傳回結合在這個節點下的執行資源數目。|
|[I拓撲節點:取得第一個執行資源](#getfirstexecutionresource)|傳回依列舉順序在這個節點下設為群組的第一個執行資源。|
|[I拓撲節點:GetId](#getid)|返回資源管理員對此節點的唯一標識符。|
|[I拓撲節點:取得下一個](#getnext)|讓介面返回列舉順序中的下一個拓撲節點。|
|[I拓撲節點::取得NumaNode](#getnumanode)|返回此資源馬anger節點所屬的Windows分配的NUMA節點號。|

## <a name="remarks"></a>備註

此介面通常用於遍歷資源管理器觀察到的系統拓撲。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`ITopologyNode`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>I拓撲節點:取得執行資源計數方法

傳回結合在這個節點下的執行資源數目。

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>傳回值

結合在這個節點下的執行資源數目。

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>I拓撲節點:取得第一個執行資源方法

傳回依列舉順序在這個節點下設為群組的第一個執行資源。

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>傳回值

依列舉順序在這個節點下設為群組的第一個執行資源。

## <a name="itopologynodegetid-method"></a><a name="getid"></a>I拓撲節點:GetId 方法

返回資源管理員對此節點的唯一標識符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

資源管理員對此節點的唯一標識符。

### <a name="remarks"></a>備註

併發運行時以處理器節點組表示系統上的硬體線程。 節點通常派生自系統的硬體拓撲。 例如,特定套接字或特定 NUMA 節點上的所有處理器可能屬於同一處理器節點。 資源管理器為這些節點分配唯一標識符,從`0`最多和`nodeCount - 1`包括 開始`nodeCount`,其中 表示系統上的處理器節點總數。

節點計數可以從函數[GetProcessorNodeCount](concurrency-namespace-functions.md)獲得。

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>I拓撲節點:取得下一個方法

讓介面返回列舉順序中的下一個拓撲節點。

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>傳回值

介面返回列舉順序中的下一個節點。 如果系統拓撲的列舉順序中沒有其他節點，這個方法將傳回值 `NULL`。

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>I拓撲節點::取得NumaNode方法

返回此資源馬anger節點所屬的Windows分配的NUMA節點號。

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>傳回值

此資源管理員節點所屬的 Windows 分配了 NUMA 節點號。

### <a name="remarks"></a>備註

在屬於此節點的虛擬處理器根上運行的線程代理將至少具有此方法返回的 NUMA 節點的 NUMA 節點等級的關聯。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

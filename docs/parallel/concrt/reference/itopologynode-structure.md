---
title: ITopologyNode 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4168fbfbd2bf17ad8b8b752d2843c8f57b0f3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692687"
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
|[ITopologyNode::GetId](#getid)|傳回這個節點的資源管理員的唯一識別碼。|  
|[ITopologyNode::GetNext](#getnext)|讓介面返回列舉順序中的下一個拓撲節點。|  
|[ITopologyNode::GetNumaNode](#getnumanode)|傳回 Windows 指派給這個資源管理員節點所屬的 NUMA 節點數目。|  
  
## <a name="remarks"></a>備註  
 通常利用此介面為觀察到由資源管理員逐步系統的拓撲。  
  
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
 傳回這個節點的資源管理員的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 資源管理員的此節點的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 並行執行階段代表硬體執行緒的處理器節點群組中的系統上。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都屬於在相同處理器節點。 資源管理員會將唯一識別項指派給這些節點從開始`0`最多並包括`nodeCount - 1`，其中`nodeCount`代表處理器在系統上的節點總數。  
  
 您可以從函式取得的節點數目[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
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
 Windows 會指派到這個資源管理員節點所屬的 NUMA 節點數目。  
  
### <a name="remarks"></a>備註  
 屬於此節點虛擬處理器根上執行的執行緒 proxy 必須至少為親和性的 NUMA 節點，這個方法所傳回的 NUMA 節點層級。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

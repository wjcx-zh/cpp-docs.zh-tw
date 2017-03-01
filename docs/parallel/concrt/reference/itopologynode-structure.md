---
title: "ITopologyNode 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::ITopologyNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 8274da148f9f74cad73d63363bbbaff307943539
ms.lasthandoff: 02/24/2017

---
# <a name="itopologynode-structure"></a>ITopologyNode 結構
資源管理員所定義的拓撲節點介面。 節點可包含一個或多個執行資源。  
  
## <a name="syntax"></a>語法  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Itopologynode:: Getexecutionresourcecount 方法](#getexecutionresourcecount)|傳回結合在這個節點下的執行資源數目。|  
|[Itopologynode:: Getfirstexecutionresource 方法](#getfirstexecutionresource)|傳回依列舉順序在這個節點下設為群組的第一個執行資源。|  
|[Itopologynode:: Getid 方法](#getid)|傳回這個節點的資源管理員的唯一識別碼。|  
|[Itopologynode:: Getnext 方法](#getnext)|讓介面返回列舉順序中的下一個拓撲節點。|  
|[Itopologynode:: Getnumanode 方法](#getnumanode)|傳回 Windows 指派給這個資源管理員節點所屬的 NUMA 節點編號。|  
  
## <a name="remarks"></a>備註  
 此介面通常可以利用來引導系統的拓撲，觀察到由資源管理員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ITopologyNode`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namegetexecutionresourcecounta--itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>Itopologynode:: Getexecutionresourcecount 方法  
 傳回結合在這個節點下的執行資源數目。  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 結合在這個節點下的執行資源數目。  
  
##  <a name="a-namegetfirstexecutionresourcea--itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>Itopologynode:: Getfirstexecutionresource 方法  
 傳回依列舉順序在這個節點下設為群組的第一個執行資源。  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 依列舉順序在這個節點下設為群組的第一個執行資源。  
  
##  <a name="a-namegetida--itopologynodegetid-method"></a><a name="getid"></a>Itopologynode:: Getid 方法  
 傳回這個節點的資源管理員的唯一識別碼。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 資源管理員的這個節點的唯一識別碼。  
  
### <a name="remarks"></a>備註  
 並行執行階段代表硬體執行緒的處理器節點群組中的系統上。 節點通常衍生自系統的硬體拓撲。 例如，在特定的通訊端或特定的 NUMA 節點上的所有處理器可能都隸屬於相同處理器節點。 資源管理員會將唯一識別項指派給這些節點從開始`0`最多並包括`nodeCount - 1`，其中`nodeCount`代表系統上的處理器節點總數。  
  
 您可以從函式取得的節點數目[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
##  <a name="a-namegetnexta--itopologynodegetnext-method"></a><a name="getnext"></a>Itopologynode:: Getnext 方法  
 讓介面返回列舉順序中的下一個拓撲節點。  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 介面返回列舉順序中的下一個節點。 如果系統拓撲的列舉順序中沒有其他節點，這個方法將傳回值 `NULL`。  
  
##  <a name="a-namegetnumanodea--itopologynodegetnumanode-method"></a><a name="getnumanode"></a>Itopologynode:: Getnumanode 方法  
 傳回 Windows 指派給這個資源管理員節點所屬的 NUMA 節點編號。  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 Windows 指派給這個資源管理員節點所屬的 NUMA 節點編號。  
  
### <a name="remarks"></a>備註  
 屬於這個節點的虛擬處理器根上執行的執行緒 proxy 會有同質至少為這個方法所傳回的 NUMA 節點的 NUMA 節點層級。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


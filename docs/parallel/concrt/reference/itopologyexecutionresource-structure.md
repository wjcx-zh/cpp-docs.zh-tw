---
title: "ITopologyExecutionResource 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs: C++
helpviewer_keywords: ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: caf2cc77cd31df611f71d07c5a0a49f600767f81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 結構
資源管理員所定義的執行資源介面。  
  
## <a name="syntax"></a>語法  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[Itopologyexecutionresource:: Getid](#getid)|傳回這個執行資源的資源管理員唯一識別項。|  
|[Itopologyexecutionresource:: Getnext](#getnext)|讓介面返回列舉順序中的下一個執行資源。|  
  
## <a name="remarks"></a>備註  
 通常利用此介面為觀察到由資源管理員逐步系統的拓撲。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="getid"></a>Itopologyexecutionresource:: Getid 方法  
 傳回這個執行資源的資源管理員唯一識別項。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 這個執行資源的資源管理員唯一識別項。  
  
##  <a name="getnext"></a>Itopologyexecutionresource:: Getnext 方法  
 讓介面返回列舉順序中的下一個執行資源。  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 介面返回列舉順序中的下一個執行資源。 如果節點的列舉順序中沒有這個執行資源所屬的其他節點，這個方法將傳回值 `NULL`。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

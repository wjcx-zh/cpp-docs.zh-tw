---
title: "ITopologyExecutionResource 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::ITopologyExecutionResource
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
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
ms.openlocfilehash: cc54beb4790c9d2ea5bfcb2c8ffd4bca7dca399e
ms.lasthandoff: 02/24/2017

---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 結構
資源管理員所定義的執行資源介面。  
  
## <a name="syntax"></a>語法  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[Itopologyexecutionresource:: Getid 方法](#getid)|傳回這個執行資源的資源管理員唯一識別項。|  
|[Itopologyexecutionresource:: Getnext 方法](#getnext)|讓介面返回列舉順序中的下一個執行資源。|  
  
## <a name="remarks"></a>備註  
 此介面通常可以利用來引導系統的拓撲，觀察到由資源管理員。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrtrm.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namegetida--itopologyexecutionresourcegetid-method"></a><a name="getid"></a>Itopologyexecutionresource:: Getid 方法  
 傳回這個執行資源的資源管理員唯一識別項。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 這個執行資源的資源管理員唯一識別項。  
  
##  <a name="a-namegetnexta--itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>Itopologyexecutionresource:: Getnext 方法  
 讓介面返回列舉順序中的下一個執行資源。  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>傳回值  
 介面返回列舉順序中的下一個執行資源。 如果節點的列舉順序中沒有這個執行資源所屬的其他節點，這個方法將傳回值 `NULL`。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


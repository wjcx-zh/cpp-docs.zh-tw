---
title: "static_partitioner 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs: C++
helpviewer_keywords: static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c7f41a2d2a592bff5e1f2217b39b6047d5093ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="staticpartitioner-class"></a>static_partitioner 類別
`static_partitioner` 類別表示由 `parallel_for` 逐一查看之範圍的靜態分割。 Partitioner 會將範圍分成許多區塊，其數量與基礎排程器可用的背景工作數量相等。  
  
## <a name="syntax"></a>語法  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[static_partitioner](#ctor)|建構 `static_partitioner` 物件。|  
|[~ static_partitioner 解構函式](#dtor)|終結 `static_partitioner` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `static_partitioner`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppl.h  
  
 **命名空間：** concurrency  
  
##  <a name="dtor"></a>~ static_partitioner 

 終結 `static_partitioner` 物件。  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a>static_partitioner 

 建構 `static_partitioner` 物件。  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

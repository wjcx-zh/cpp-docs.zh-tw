---
title: "scheduler_interface 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
dev_langs:
- C++
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 042457c83486cbefe863ec35a539d53c95b316a2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="schedulerinterface-structure"></a>scheduler_interface 結構
排程器介面  
  
## <a name="syntax"></a>語法  
  
```
struct __declspec(novtable) scheduler_interface;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_interface::schedule](#schedule)||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `scheduler_interface`  
  
## <a name="requirements"></a>需求  
 **標頭：** pplinterface.h  
  
 **命名空間：** concurrency  
  
##  <a name="schedule"></a>  scheduler_interface:: schedule 方法  
  
```
virtual void schedule(
    TaskProc_t,
 void*) = 0;
```  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

---
title: "invalid_multiple_scheduling 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling
- CONCRT/concurrency::invalid_multiple_scheduling::invalid_multiple_scheduling
dev_langs:
- C++
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7aed5586f58560e01b1a22f973ab7defadf49432
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling 類別
這個類別描述使用 `task_group` 或 `structured_task_group` 物件的 `run` 方法多次排程 `task_handle` 物件，而不中間變更呼叫 `wait` 或 `run_and_wait` 方法時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[invalid_multiple_scheduling](#ctor)|多載。 建構 `invalid_multiple_scheduling` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> invalid_multiple_scheduling 

 建構 `invalid_multiple_scheduling` 物件。  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_handle 類別](task-handle-class.md)   
 [task_group 類別](task-group-class.md)   
 [run](task-group-class.md)   
 [wait](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group 類別](structured-task-group-class.md)

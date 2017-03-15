---
title: "invalid_multiple_scheduling 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_multiple_scheduling
dev_langs:
- C++
helpviewer_keywords:
- invalid_multiple_scheduling class
ms.assetid: e9a47cb7-a778-4df7-92b0-3752119fd4c7
caps.latest.revision: 19
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 762648e65a7fcbda29daf31412e42bbd0e63f3d6
ms.lasthandoff: 02/24/2017

---
# <a name="invalidmultiplescheduling-class"></a>invalid_multiple_scheduling 類別
這個類別描述使用 `task_group` 或 `structured_task_group` 物件的 `run` 方法多次排程 `task_handle` 物件，而不中間變更呼叫 `wait` 或 `run_and_wait` 方法時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_multiple_scheduling : public std::exception;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[invalid_multiple_scheduling 建構函式](#ctor)|多載。 建構 `invalid_multiple_scheduling` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_multiple_scheduling`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-invalidmultiplescheduling"></a><a name="ctor"></a>invalid_multiple_scheduling 

 建構 `invalid_multiple_scheduling` 物件。  
  
```
explicit _CRTIMP invalid_multiple_scheduling(_In_z_ const char* _Message) throw();

invalid_multiple_scheduling() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_handle 類別](task-handle-class.md)   
 [task_group 類別](task-group-class.md)   
 [run 方法](task-group-class.md)   
 [wait 方法](task-group-class.md)   
 [run_and_wait 方法](task-group-class.md)   
 [structured_task_group 類別](structured-task-group-class.md)


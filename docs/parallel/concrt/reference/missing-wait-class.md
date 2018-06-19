---
title: missing_wait 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- missing_wait
- CONCRT/concurrency::missing_wait
- CONCRT/concurrency::missing_wait::missing_wait
dev_langs:
- C++
helpviewer_keywords:
- missing_wait class
ms.assetid: ff981875-bd43-47e3-806f-b03c9f418b18
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5ebd607dc207975e7d38e3217c275d3d5d18bb8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686343"
---
# <a name="missingwait-class"></a>missing_wait 類別
這個類別描述 `task_group` 或 `structured_task_group` 物件的建構函式執行時卻仍有工作排程至該物件所擲回的例外狀況。 如果例外狀況導致堆疊回溯而達成解構函式，則永遠不會擲回此例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class missing_wait : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[missing_wait](#ctor)|多載。 建構 `missing_wait` 物件。|  
  
## <a name="remarks"></a>備註  
 不存在的例外狀況流程，您必須負責呼叫`wait`或`run_and_wait`方法`task_group`或`structured_task_group`之前允許該物件解構的物件。 執行階段會擲回這個例外狀況，表示您忘了呼叫`wait`或`run_and_wait`方法。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `missing_wait`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> missing_wait 

 建構 `missing_wait` 物件。  
  
```
explicit _CRTIMP missing_wait(_In_z_ const char* _Message) throw();

missing_wait() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [task_group 類別](task-group-class.md)   
 [等候](task-group-class.md)   
 [run_and_wait](task-group-class.md)   
 [structured_task_group 類別](structured-task-group-class.md)

---
title: "nested_scheduler_missing_detach 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::nested_scheduler_missing_detach
dev_langs:
- C++
helpviewer_keywords:
- nested_scheduler_missing_detach class
ms.assetid: 65d3f277-6d43-4160-97ef-caf8b26c1641
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
ms.openlocfilehash: 0079fea0b157e194947931f88d1cb500167cb6e2
ms.lasthandoff: 02/24/2017

---
# <a name="nestedschedulermissingdetach-class"></a>nested_scheduler_missing_detach 類別
這個類別描述當並行執行階段偵測到您忘了使用 `Scheduler` 物件的 `Attach` 方法在附加到第二個排程器上呼叫 `CurrentScheduler::Detach` 方法時擲出的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class nested_scheduler_missing_detach : public std::exception;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[nested_scheduler_missing_detach 建構函式](#ctor)|多載。 建構 `nested_scheduler_missing_detach` 物件。|  
  
## <a name="remarks"></a>備註  
 當您在已由其他排程器擁有或附加的內容上呼叫 `Attach` 物件的`Scheduler` 方法，將排程器巢狀排列在另一個排程器內時，才會擲回這個例外狀況。 並行執行階段會擲回這個例外狀況 」 時，它可以偵測案例來協助找出問題。 並非每個執行個體上隻字未呼叫`CurrentScheduler::Detach`方法一定會擲回這個例外狀況。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `nested_scheduler_missing_detach`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-nestedschedulermissingdetach"></a><a name="ctor"></a>nested_scheduler_missing_detach 

 建構 `nested_scheduler_missing_detach` 物件。  
  
```
explicit _CRTIMP nested_scheduler_missing_detach(_In_z_ const char* _Message) throw();

nested_scheduler_missing_detach() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)


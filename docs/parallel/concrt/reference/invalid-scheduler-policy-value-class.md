---
title: "invalid_scheduler_policy_value 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
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
ms.openlocfilehash: ff5b07b62923a289da1b47de08b527da212e4a2d
ms.lasthandoff: 02/24/2017

---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value 類別
這個類別描述在將 `SchedulerPolicy` 物件的原則機碼設為不正確的機碼值時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[invalid_scheduler_policy_value 建構函式](invalid-scheduler-policy-thread-specification-class.md#ctor|多載。 建構 `invalid_scheduler_policy_value` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
    
##  <a name="a-namectora-invalidschedulerpolicyvalue"></a><a name="ctor"></a>invalid_scheduler_policy_value 

 建構 `invalid_scheduler_policy_value` 物件。  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  

## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [SchedulerPolicy 類別](schedulerpolicy-class.md)


---
title: "invalid_scheduler_policy_value 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- concrt/concurrency::invalid_scheduler_policy_value
dev_langs:
- C++
helpviewer_keywords:
- invalid_scheduler_policy_value class
ms.assetid: 8c533e3f-2774-4192-8616-b2313b859bf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbcbef5fc97f10b923b9a6b692a7cfa3799151b0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="invalidschedulerpolicyvalue-class"></a>invalid_scheduler_policy_value 類別
這個類別描述在將 `SchedulerPolicy` 物件的原則機碼設為不正確的機碼值時擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_scheduler_policy_value : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[invalid_scheduler_policy_value](invalid-scheduler-policy-thread-specification-class.md#ctor|多載。 建構 `invalid_scheduler_policy_value` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_scheduler_policy_value`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
    
##  <a name="ctor"></a> invalid_scheduler_policy_value 

 建構 `invalid_scheduler_policy_value` 物件。  
  
```
explicit _CRTIMP invalid_scheduler_policy_value(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_value() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  

## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [SchedulerPolicy 類別](schedulerpolicy-class.md)

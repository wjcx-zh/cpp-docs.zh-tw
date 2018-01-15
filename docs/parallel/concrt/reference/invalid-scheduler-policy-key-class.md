---
title: "invalid_scheduler_policy_key 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key
- CONCRT/concurrency::invalid_scheduler_policy_key::invalid_scheduler_policy_key
dev_langs: C++
helpviewer_keywords: invalid_scheduler_policy_key class
ms.assetid: 6a7c42fe-9bc4-4a02-bebb-99fe9ef9817d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8de8f3a9a027a1b9ae4862d21e27a45f110047b4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="invalidschedulerpolicykey-class"></a>invalid_scheduler_policy_key 類別
這個類別描述將無效或未知的機碼傳遞給 `SchedulerPolicy` 物件建構函式，或將必須使用其他方式 (如 `SetConcurrencyLimits` 方法) 變更的機碼傳遞給 `SchedulerPolicy` 物件的 `SetPolicyValue` 方法時所擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class invalid_scheduler_policy_key : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[invalid_scheduler_policy_key](#ctor)|多載。 建構 `invalid_scheduler_policy_key` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `invalid_scheduler_policy_key`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a>invalid_scheduler_policy_key 

 建構 `invalid_scheduler_policy_key` 物件。  
  
```
explicit _CRTIMP invalid_scheduler_policy_key(_In_z_ const char* _Message) throw();

invalid_scheduler_policy_key() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [SchedulerPolicy 類別](schedulerpolicy-class.md)

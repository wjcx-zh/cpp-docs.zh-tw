---
title: "improper_scheduler_detach 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach
- CONCRT/concurrency::improper_scheduler_detach::improper_scheduler_detach
dev_langs:
- C++
helpviewer_keywords:
- improper_scheduler_detach class
ms.assetid: 30132102-c900-4951-a470-b63b4e3aa2d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b0a11ed3d65403444c62147091f443d3f102676
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="improperschedulerdetach-class"></a>improper_scheduler_detach 類別
這個類別描述當尚未使用 `Scheduler` 物件的 `Attach` 方法將內容附加至任何排程器時呼叫 `CurrentScheduler::Detach` 方法所擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class improper_scheduler_detach : public std::exception;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[improper_scheduler_detach](#ctor)|多載。 建構 `improper_scheduler_detach` 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 `improper_scheduler_detach`  
  
## <a name="requirements"></a>需求  
 **標頭：** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="ctor"></a> improper_scheduler_detach 

 建構 `improper_scheduler_detach` 物件。  
  
```
explicit _CRTIMP improper_scheduler_detach(_In_z_ const char* _Message) throw();

improper_scheduler_detach() throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
## <a name="see-also"></a>請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [Scheduler 類別](scheduler-class.md)

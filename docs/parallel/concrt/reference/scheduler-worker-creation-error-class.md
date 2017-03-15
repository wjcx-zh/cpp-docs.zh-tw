---
title: "scheduler_worker_creation_error 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::scheduler_worker_creation_error
dev_langs:
- C++
helpviewer_keywords:
- scheduler_worker_creation_error class
ms.assetid: 4aec1c3e-c32a-41b2-899d-2d898f23b3c7
caps.latest.revision: 9
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
ms.openlocfilehash: c880ed65ef9e01c7eebdd2de45598a41763da57c
ms.lasthandoff: 02/24/2017

---
# <a name="schedulerworkercreationerror-class"></a>scheduler_worker_creation_error 類別
這個類別描述因為無法建立並行執行階段中的背景工作執行內容而擲回的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```
class scheduler_worker_creation_error : public scheduler_resource_allocation_error;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[scheduler_worker_creation_error 建構函式](#ctor)|多載。 建構 `scheduler_worker_creation_error` 物件。|  
  
## <a name="remarks"></a>備註  
 這個例外狀況通常是在從並行執行階段內呼叫作業系統建立執行內容失敗時擲回。 執行內容是指在並行執行階段的工作中執行的執行緒。 通常會從呼叫 Win32 方法 `GetLastError` 傳回的錯誤碼會轉換成 `HRESULT` 類型的值，並且可以使用基底類別方法 `get_error_code` 擷取。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `exception`  
  
 [scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)  
  
 `scheduler_worker_creation_error`  
  
## <a name="requirements"></a>需求  
 **標頭︰** concrt.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namectora-schedulerworkercreationerror"></a><a name="ctor"></a>scheduler_worker_creation_error 

 建構 `scheduler_worker_creation_error` 物件。  
  
```
scheduler_worker_creation_error(
    _In_z_ const char* _Message,
    HRESULT _Hresult) throw();

explicit _CRTIMP scheduler_worker_creation_error(
    HRESULT _Hresult) throw();
```  
  
### <a name="parameters"></a>參數  
 `_Message`  
 錯誤的描述性訊息。  
  
 `_Hresult`  
 `HRESULT`造成例外狀況之錯誤的值。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


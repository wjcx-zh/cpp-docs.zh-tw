---
title: "message_processor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
dev_langs:
- C++
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: dff934584179cc58d884be65fdb96cb6c646a4ac
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="messageprocessor-class"></a>message_processor 類別
`message_processor` 類別是處理 `message` 物件的抽象基底類別。 訊息順序方面沒有一定的保證。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class message_processor;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 在訊息中裝載的資料型別由這`message_processor`物件。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`type`|類型別名`T`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[async_send](#async_send)|在衍生類別中覆寫，將訊息置於區塊以非同步的方式。|  
|[sync_send](#sync_send)|在衍生類別中覆寫，將訊息置於區塊以同步方式。|  
|[等候](#wait)|當在衍生類別中覆寫時，會等到所有非同步作業完成。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[process_incoming_message](#process_incoming_message)|當在衍生類別中覆寫時，會執行到區塊轉寄訊息的處理。 每次新增了新的訊息，並發現佇列是空的呼叫一次。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `message_processor`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="async_send"></a>async_send 

 在衍生類別中覆寫，將訊息置於區塊以非同步的方式。  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 A`message`以非同步方式傳送物件。  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
##  <a name="process_incoming_message"></a>process_incoming_message 

 當在衍生類別中覆寫時，會執行到區塊轉寄訊息的處理。 每次新增了新的訊息，並發現佇列是空的呼叫一次。  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>備註  
 訊息區塊實作應該覆寫這個方法。  
  
##  <a name="sync_send"></a>sync_send 

 在衍生類別中覆寫，將訊息置於區塊以同步方式。  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 A`message`要以同步方式傳送物件。  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
##  <a name="wait"></a>等候 

 當在衍生類別中覆寫時，會等到所有非同步作業完成。  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ordered_message_processor 類別](ordered-message-processor-class.md)


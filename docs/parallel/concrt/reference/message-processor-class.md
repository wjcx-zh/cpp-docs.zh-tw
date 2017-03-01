---
title: "message_processor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::message_processor
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 98f1c1072916c4cf3670e40ce0c6ddd1a17f1b63
ms.lasthandoff: 02/24/2017

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
  
|名稱|說明|  
|----------|-----------------|  
|`type`|類型別名`T`。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[async_send 方法](#async_send)|在衍生類別中覆寫，將訊息置於區塊以非同步的方式。|  
|[sync_send 方法](#sync_send)|在衍生類別中覆寫，將訊息置於區塊以同步方式。|  
|[wait 方法](#wait)|當在衍生類別中覆寫時，會等到所有非同步作業完成。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|說明|  
|----------|-----------------|  
|[process_incoming_message 方法](#process_incoming_message)|當在衍生類別中覆寫時，會執行到區塊轉寄訊息的處理。 每次新增了新的訊息，並發現佇列是空的呼叫一次。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `message_processor`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-nameasyncsenda-asyncsend"></a><a name="async_send"></a>async_send 

 在衍生類別中覆寫，將訊息置於區塊以非同步的方式。  
  
```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 A`message`以非同步方式傳送物件。  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
##  <a name="a-nameprocessincomingmessagea-processincomingmessage"></a><a name="process_incoming_message"></a>process_incoming_message 

 當在衍生類別中覆寫時，會執行到區塊轉寄訊息的處理。 每次新增了新的訊息，並發現佇列是空的呼叫一次。  
  
```
virtual void process_incoming_message() = 0;
```  
  
### <a name="remarks"></a>備註  
 訊息區塊實作應該覆寫這個方法。  
  
##  <a name="a-namesyncsenda-syncsend"></a><a name="sync_send"></a>sync_send 

 在衍生類別中覆寫，將訊息置於區塊以同步方式。  
  
```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```  
  
### <a name="parameters"></a>參數  
 `_Msg`  
 A`message`要以同步方式傳送物件。  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
##  <a name="a-namewaita-wait"></a><a name="wait"></a>等候 

 當在衍生類別中覆寫時，會等到所有非同步作業完成。  
  
```
virtual void wait() = 0;
```  
  
### <a name="remarks"></a>備註  
 處理器實作應該覆寫這個方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)   
 [ordered_message_processor 類別](ordered-message-processor-class.md)


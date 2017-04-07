---
title: "message 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
dev_langs:
- C++
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
caps.latest.revision: 21
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: c6cc72c1fe9385eabe86194031913b7363d602ff
ms.lasthandoff: 03/17/2017

---
# <a name="message-class"></a>message 類別
基本訊息封套，其中包含在傳訊區塊之間傳遞的資料承載。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 訊息內的內容資料型別。  
  
## <a name="members"></a>Members  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`type`|類型別名`T`。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[message](#ctor)|多載。 建構 `message` 物件。|  
|[~ message 解構函式](#dtor)|終結`message`物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[add_ref](#add_ref)|加入的參考計數`message`物件。 用於需要參考計數來決定訊息的存留期的訊息區塊。|  
|[msg_id](#msg_id)|傳回的識別碼`message`物件。|  
|[remove_ref](#remove_ref)|參考計數中減去`message`物件。 用於需要參考計數來決定訊息的存留期的訊息區塊。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[裝載](#payload)|封包承載`message`物件。|  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[非同步訊息區](../../../parallel/concrt/asynchronous-message-blocks.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `message`  
  
## <a name="requirements"></a>需求  
 **標頭：** agents.h  
  
 **命名空間：** concurrency  
  
##  <a name="add_ref"></a>add_ref 

 加入的參考計數`message`物件。 用於需要參考計數來決定訊息的存留期的訊息區塊。  
  
```
long add_ref();
```  
  
### <a name="return-value"></a>傳回值  
 參考計數的新值。  
  
##  <a name="ctor"></a>訊息 

 建構 `message` 物件。  
  
```
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```  
  
### <a name="parameters"></a>參數  
 `_P`  
 此訊息的內容。  
  
 `_Id`  
 這個訊息的唯一 ID。  
  
 `_Msg`  
 參考或指標`message`物件。  
  
### <a name="remarks"></a>備註  
 建構函式的指標之`message`物件引數則會擲回[invalid_argument](../../../standard-library/invalid-argument-class.md)例外狀況如果參數`_Msg`是`NULL`。  
  
##  <a name="dtor"></a>~ 訊息 

 終結`message`物件。  
  
```
virtual ~message();
```  
  
##  <a name="msg_id"></a>msg_id 

 傳回的識別碼`message`物件。  
  
```
runtime_object_identity msg_id() const;
```  
  
### <a name="return-value"></a>傳回值  
 `runtime_object_identity`的`message`物件。  
  
##  <a name="payload"></a>裝載 

 封包承載`message`物件。  
  
```
T const payload;
```  
  
##  <a name="remove_ref"></a>remove_ref 

 參考計數中減去`message`物件。 用於需要參考計數來決定訊息的存留期的訊息區塊。  
  
```
long remove_ref();
```  
  
### <a name="return-value"></a>傳回值  
 參考計數的新值。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


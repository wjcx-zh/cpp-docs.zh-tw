---
title: "cancellation_token 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pplcancellation_token/concurrency::cancellation_token
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
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
ms.openlocfilehash: 93d5abe132203a53f3ffac8490fe32604e7e896e
ms.lasthandoff: 02/24/2017

---
# <a name="cancellationtoken-class"></a>cancellation_token 類別
`cancellation_token` 類別表示可判斷某個作業是否已要求取消的能力。 特定語彙基元可以與 `task_group`、`structured_task_group` 或 `task` 產生關聯，來提供隱含取消作業。 如果與相關聯的 `cancellation_token_source` 已取消，也可以向它輪詢取消，或為它註冊回呼。  
  
## <a name="syntax"></a>語法  
  
```
class cancellation_token;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[cancellation_token 建構函式](#ctor)||  
|[~ cancellation_token 解構函式](#dtor)||  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[deregister_callback 方法](#deregister_callback)|根據註冊時傳回的 `register` 物件，移除先前透過 `cancellation_token_registration` 方法註冊的回呼。|  
|[is_cancelable 方法](#is_cancelable)|傳回這個語彙基元是否可以取消的指示。|  
|[is_canceled 方法](#is_canceled)|如果語彙基元已取消，則傳回 `true`。|  
|[none 方法](#none)|傳回永不需取消的取消語彙基元。|  
|[register_callback 方法](#register_callback)|使用語彙基元註冊回呼函式。 如果這個語彙基元已取消，將會進行回呼。 請注意，如果語彙基元已經在呼叫此方法的時間點取消，將會立即同步進行回呼。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 ！ = 運算子](#operator_neq)||  
|[運算子 = 運算子](#operator_eq)||  
|[運算子 = = 運算子](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `cancellation_token`  
  
## <a name="requirements"></a>需求  
 **標頭︰** pplcancellation_token.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namedtora-cancellationtoken"></a><a name="dtor"></a>~ cancellation_token 

```
~cancellation_token();
```  
  
##  <a name="a-namectora-cancellationtoken"></a><a name="ctor"></a>cancellation_token 

```
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
##  <a name="a-namederegistercallbacka-deregistercallback"></a><a name="deregister_callback"></a>deregister_callback 

 根據註冊時傳回的 `register` 物件，移除先前透過 `cancellation_token_registration` 方法註冊的回呼。  
  
```
void deregister_callback(const cancellation_token_registration& _Registration) const;
```  
  
### <a name="parameters"></a>參數  
 `_Registration`  
 `cancellation_token_registration` 物件，對應於要取消註冊的回呼。 這個語彙基元必須已經由 `register` 方法呼叫所傳回。  
  
##  <a name="a-nameiscancelablea-iscancelable"></a><a name="is_cancelable"></a>is_cancelable 

 傳回這個語彙基元是否可以取消的指示。  
  
```
bool is_cancelable() const;
```  
  
### <a name="return-value"></a>傳回值  
 表示這個語彙基元是否可以取消。  
  
##  <a name="a-nameiscanceleda-iscanceled"></a><a name="is_canceled"></a>is_canceled 

 如果語彙基元已取消，則傳回 `true`。  
  
```
bool is_canceled() const;
```  
  
### <a name="return-value"></a>傳回值  
 如果語彙基元被取消，則為 `true` 值，否則為 `false` 值。  
  
##  <a name="a-namenonea-none"></a><a name="none"></a>無 

 傳回永不需取消的取消語彙基元。  
  
```
static cancellation_token none();
```  
  
### <a name="return-value"></a>傳回值  
 無法取消的取消語彙基元。  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>運算子 ！ = 

```
bool operator!= (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

```
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>運算子 = = 

```
bool operator== (const cancellation_token& _Src) const;
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameregistercallbacka-registercallback"></a><a name="register_callback"></a>register_callback 

 使用語彙基元註冊回呼函式。 如果這個語彙基元已取消，將會進行回呼。 請注意，如果語彙基元已經在呼叫此方法的時間點取消，將會立即同步進行回呼。  
  
```
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```  
  
### <a name="parameters"></a>參數  
 `_Function`  
 當取消這個 `cancellation_token` 時，會被回呼的函式物件的類型。  
  
 `_Func`  
 當取消這個 `cancellation_token` 時，會被回呼的函式物件。  
  
### <a name="return-value"></a>傳回值  
 `cancellation_token_registration` 物件，可在 `deregister` 方法中用來取消註冊先前註冊的回呼，並防止進行此回呼。 方法會擲回[invalid_operation](invalid-operation-class.md)例外狀況，如果呼叫上`cancellation_token`使用所建立的物件[cancellation_token:: none](#none)方法。  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


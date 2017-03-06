---
title: "cancellation_token_registration 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- pplcancellation_token/concurrency::cancellation_token_registration
dev_langs:
- C++
helpviewer_keywords:
- cancellation_token_registration class
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
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
ms.openlocfilehash: 72c317bb95b646a3a97b361ac3248f015cd0f29a
ms.lasthandoff: 02/24/2017

---
# <a name="cancellationtokenregistration-class"></a>cancellation_token_registration 類別
`cancellation_token_registration` 類別表示來自 `cancellation_token` 的回呼通知。 當 `register` 的 `cancellation_token` 方法用來接收發生取消的通知時，則會傳回 `cancellation_token_registration` 物件做為回呼的控制代碼，讓呼叫端可以要求不再透過使用 `deregister` 方法發出的特定回呼。  
  
## <a name="syntax"></a>語法  
  
```
class cancellation_token_registration;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[cancellation_token_registration 建構函式](#ctor)||  
|[~ cancellation_token_registration 解構函式](#dtor)||  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[運算子 ！ = 運算子](#operator_neq)||  
|[運算子 = 運算子](#operator_eq)||  
|[運算子 = = 運算子](#operator_eq_eq)||  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `cancellation_token_registration`  
  
## <a name="requirements"></a>需求  
 **標頭︰** pplcancellation_token.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namedtora-cancellationtokenregistration"></a><a name="dtor"></a>~ cancellation_token_registration 

```
~cancellation_token_registration();
```  
  
##  <a name="a-namectora-cancellationtokenregistration"></a><a name="ctor"></a>cancellation_token_registration 

```
cancellation_token_registration();

cancellation_token_registration(const cancellation_token_registration& _Src);

cancellation_token_registration(cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>運算子 ！ = 

```
bool operator!= (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>運算子 = 

```
cancellation_token_registration& operator= (const cancellation_token_registration& _Src);

cancellation_token_registration& operator= (cancellation_token_registration&& _Src);
```  
  
### <a name="parameters"></a>參數  
 `_Src`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>運算子 = = 

```
bool operator== (const cancellation_token_registration& _Rhs) const;
```  
  
### <a name="parameters"></a>參數  
 `_Rhs`  
  
### <a name="return-value"></a>傳回值  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


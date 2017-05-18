---
title: "scheduler_ptr 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
caps.latest.revision: 8
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
ms.openlocfilehash: 4bef1995724d078c9702669806ff61d5563ac465
ms.contentlocale: zh-tw
ms.lasthandoff: 03/17/2017

---
# <a name="schedulerptr-structure"></a>scheduler_ptr 結構
代表排程器的指標。 這個類別是為了允許使用 shared_ptr 共用存留期的規格，或只是使用原始指標的簡單參考。  
  
## <a name="syntax"></a>語法  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_ptr:: scheduler_ptr](#ctor)|多載。 從排程器 shared_ptr 建立排程器指標|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_ptr:: get](#get)|傳回排程器的原始指標|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[scheduler_ptr:: operator bool](#operator_bool)|測試排程器指標是否為非 null|  
|[scheduler_ptr::-&gt;](#operator_ptr)|作用如同指標|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `scheduler_ptr`  
  
## <a name="requirements"></a>需求  
 **標頭︰** pplinterface.h  
  
 **命名空間：** concurrency  
  
##  <a name="get"></a>scheduler_ptr:: get 方法  
 傳回排程器的原始指標  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="operator_bool"></a>scheduler_ptr:: operator bool   
 測試排程器指標是否為非 null  
  
'' 運算子 bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface * operator->() const;
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
明確 scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);</scheduler_interface>

明確 scheduler_ptr (_In_opt_ scheduler_interface * pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)


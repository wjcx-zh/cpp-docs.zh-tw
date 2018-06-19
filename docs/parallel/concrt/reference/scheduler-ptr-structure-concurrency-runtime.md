---
title: scheduler_ptr 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
dev_langs:
- C++
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 672e4a0dd5f66ab613dde8877915c799d6c4b2f4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686980"
---
# <a name="schedulerptr-structure"></a>scheduler_ptr 結構
代表排程器的指標。 這個類別是為了允許使用 shared_ptr 共用存留期的規格，或只是使用原始指標的簡單參考。  
  
## <a name="syntax"></a>語法  
  
```
struct scheduler_ptr;
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_ptr::scheduler_ptr](#ctor)|多載。 從排程器 shared_ptr 建立排程器指標|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_ptr::get](#get)|傳回排程器的原始指標|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[scheduler_ptr:: operator bool](#operator_bool)|測試排程器指標是否為非 null|  
|[scheduler_ptr::operator-&gt;](#operator_ptr)|作用如同指標|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `scheduler_ptr`  
  
## <a name="requirements"></a>需求  
 **標頭：** pplinterface.h  
  
 **命名空間：** concurrency  
  
##  <a name="get"></a>  scheduler_ptr:: get 方法  
 傳回排程器的原始指標  
  
```
scheduler_interface* get() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="operator_bool"></a>  scheduler_ptr:: operator bool   
 測試排程器指標是否為非 null  
  
'' 運算子 bool() const;
```  
  
##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;   
 Behave like a pointer  
  
```
scheduler_interface * operator-> const; （)
```  
  
### Return Value  
  
##  <a name="ctor"></a>  scheduler_ptr::scheduler_ptr Constructor  
 Creates a scheduler pointer from shared_ptr to scheduler  
  
```
明確 scheduler_ptr （std:: shared_ptr < scheduler_interface > 排程器）。

明確 scheduler_ptr (_In_opt_ scheduler_interface * pScheduler);
```  
  
### Parameters  
 `scheduler`  
 `pScheduler`  
  
## See Also  
 [concurrency Namespace](concurrency-namespace.md)

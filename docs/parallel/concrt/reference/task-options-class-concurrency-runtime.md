---
title: "task_options 類別 （並行執行階段） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppltasks/concurrency::task_options
dev_langs:
- C++
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
caps.latest.revision: 7
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 9b0d7d245ae204fd59715c8142a836adbb63c10a
ms.lasthandoff: 02/24/2017

---
# <a name="taskoptions-class-concurrency-runtime"></a>task_options 類別 (並行執行階段)
表示用於建立工作的允許選項  
  
## <a name="syntax"></a>語法  
  
```
class task_options;
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[task_options:: task_options 建構函式 （並行執行階段）](#ctor)|多載。 工作建立選項的預設清單|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[task_options:: get_cancellation_token 方法 （並行執行階段）](#get_cancellation_token)|傳回取消語彙基元|  
|[task_options:: get_continuation_context 方法 （並行執行階段）](#get_continuation_context)|傳回接續內容|  
|[task_options:: get_scheduler 方法 （並行執行階段）](#get_scheduler)|傳回排程器|  
|[task_options:: has_cancellation_token 方法 （並行執行階段）](#has_cancellation_token)|表示使用者是否已指定取消語彙基元|  
|[task_options:: has_scheduler 方法 （並行執行階段）](#has_scheduler)|表示使用者是否已指定排程器|  
|[task_options:: set_cancellation_token 方法 （並行執行階段）](#set_cancellation_token)|設定選項中的指定語彙基元|  
|[task_options:: set_continuation_context 方法 （並行執行階段）](#set_continuation_context)|設定選項中的指定接續內容|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_options`  
  
## <a name="requirements"></a>需求  
 **標頭︰** ppltasks.h  
  
 **命名空間：** concurrency  
  
##  <a name="a-namegetcancellationtokena--taskoptionsgetcancellationtoken-method-concurrency-runtime"></a><a name="get_cancellation_token"></a>task_options:: get_cancellation_token 方法 （並行執行階段）  
 傳回取消語彙基元  
  
```
cancellation_token get_cancellation_token() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namegetcontinuationcontexta--taskoptionsgetcontinuationcontext-method-concurrency-runtime"></a><a name="get_continuation_context"></a>task_options:: get_continuation_context 方法 （並行執行階段）  
 傳回接續內容  
  
```
task_continuation_context get_continuation_context() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namegetschedulera--taskoptionsgetscheduler-method-concurrency-runtime"></a><a name="get_scheduler"></a>task_options:: get_scheduler 方法 （並行執行階段）  
 傳回排程器  
  
```
scheduler_ptr get_scheduler() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namehascancellationtokena--taskoptionshascancellationtoken-method-concurrency-runtime"></a><a name="has_cancellation_token"></a>task_options:: has_cancellation_token 方法 （並行執行階段）  
 表示使用者是否已指定取消語彙基元  
  
```
bool has_cancellation_token() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namehasschedulera--taskoptionshasscheduler-method-concurrency-runtime"></a><a name="has_scheduler"></a>task_options:: has_scheduler 方法 （並行執行階段）  
 表示使用者是否已指定排程器  
  
```
bool has_scheduler() const;
```  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="a-namesetcancellationtokena--taskoptionssetcancellationtoken-method-concurrency-runtime"></a><a name="set_cancellation_token"></a>task_options:: set_cancellation_token 方法 （並行執行階段）  
 設定選項中的指定語彙基元  
  
```
void set_cancellation_token(cancellation_token _Token);
```  
  
### <a name="parameters"></a>參數  
 `_Token`  
  
##  <a name="a-namesetcontinuationcontexta--taskoptionssetcontinuationcontext-method-concurrency-runtime"></a><a name="set_continuation_context"></a>task_options:: set_continuation_context 方法 （並行執行階段）  
 設定選項中的指定接續內容  
  
```
void set_continuation_context(task_continuation_context _ContinuationContext);
```  
  
### <a name="parameters"></a>參數  
 `_ContinuationContext`  
  
##  <a name="a-namectora--taskoptionstaskoptions-constructor-concurrency-runtime"></a><a name="ctor"></a>task_options:: task_options 建構函式 （並行執行階段）  
 工作建立選項的預設清單  
  
```
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```  
  
### <a name="parameters"></a>參數  
 `_SchedType`  
 `_Token`  
 `_ContinuationContext`  
 `_Scheduler`  
 `_TaskOptions`  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)


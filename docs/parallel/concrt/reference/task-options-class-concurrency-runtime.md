---
title: task_options 類別 （並行執行階段） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ppltasks/concurrency::task_options
dev_langs:
- C++
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7dccc4fec79ad11d7d4667c93b1b9ae8362ed92
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437075"
---
# <a name="taskoptions-class-concurrency-runtime"></a>task_options 類別 (並行執行階段)

表示用於建立工作的允許選項

## <a name="syntax"></a>語法

```
class task_options;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_options:: task_options 建構函式 （並行執行階段）](#ctor)|多載。 工作建立選項的預設清單|

### <a name="public-methods"></a>公用方法

|名稱|描述|
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

**標頭：** ppltasks.h

**命名空間：** concurrency

##  <a name="get_cancellation_token"></a>  task_options:: get_cancellation_token 方法 （並行執行階段）

傳回取消語彙基元

```
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>傳回值

##  <a name="get_continuation_context"></a>  task_options:: get_continuation_context 方法 （並行執行階段）

傳回接續內容

```
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>傳回值

##  <a name="get_scheduler"></a>  task_options:: get_scheduler 方法 （並行執行階段）

傳回排程器

```
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>傳回值

##  <a name="has_cancellation_token"></a>  task_options:: has_cancellation_token 方法 （並行執行階段）

表示使用者是否已指定取消語彙基元

```
bool has_cancellation_token() const;
```

### <a name="return-value"></a>傳回值

##  <a name="has_scheduler"></a>  task_options:: has_scheduler 方法 （並行執行階段）

表示使用者是否已指定排程器

```
bool has_scheduler() const;
```

### <a name="return-value"></a>傳回值

##  <a name="set_cancellation_token"></a>  task_options:: set_cancellation_token 方法 （並行執行階段）

設定選項中的指定語彙基元

```
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>參數

`_Token`

##  <a name="set_continuation_context"></a>  task_options:: set_continuation_context 方法 （並行執行階段）

設定選項中的指定接續內容

```
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>參數

`_ContinuationContext`

##  <a name="ctor"></a>  task_options:: task_options 建構函式 （並行執行階段）

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

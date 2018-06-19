---
title: task_completion_event 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
dev_langs:
- C++
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b22b77affd41aa60769543ae2bea2ed495084ae
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687877"
---
# <a name="taskcompletionevent-class"></a>task_completion_event 類別
`task_completion_event` 類別可讓您延遲執行工作，直到滿足某條件，或是為了回應外部事件而開始工作。  
  
## <a name="syntax"></a>語法  
  
```
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```  
  
#### <a name="parameters"></a>參數  
 `_ResultType`  
 這個 `task_completion_event` 類別的結果類型。  
  
 `T`  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[task_completion_event](#ctor)|建構 `task_completion_event` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[set](#set)|多載。 設定工作完成事件。|  
|[set_exception](#set_exception)|多載。 將例外狀況傳播至與這個事件相關聯的所有工作。|  
  
## <a name="remarks"></a>備註  
 在需要您建立要完成之工作的情況下，使用從工作完成事件建立的工作，以藉此將其接續排程在未來的某個時間點執行。 `task_completion_event` 必須與您建立的工作具有相同類型，而且在具有該類型值的工作完成事件上呼叫 set 方法，將導致關聯工作完成，並將該值當做結果提供給其接續。  
  
 如果永不發出工作完成事件的信號，則當工作完成事件解構時，將會取消從中建立的所有工作。  
  
 `task_completion_event` 的行為就像智慧型指標，應該依值傳遞。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `task_completion_event`  
  
## <a name="requirements"></a>需求  
 **標頭：** ppltasks.h  
  
 **命名空間：** concurrency  
  
##  <a name="set"></a> 設定 

 設定工作完成事件。  
  
```
bool set(_ResultType _Result) const ;

bool set() const ;
```  
  
### <a name="parameters"></a>參數  
 `_Result`  
 要設定與此事件的結果。  
  
### <a name="return-value"></a>傳回值  
 方法會傳回`true`如果它已順利設定事件。 它會傳回`false`若已設定事件。  
  
### <a name="remarks"></a>備註  
 如果存在多個並行呼叫或`set`，只有第一次呼叫會成功，且其結果 （如果有的話） 會儲存在工作完成事件。 將其餘會忽略，而該方法會傳回 false。 當您設定工作完成事件時，所有工作從都建立事件將會立即完成，，和其接續，如果有的話，將排程。 工作完成的物件`_ResultType`以外`void`會將值傳遞給其接續。  
  
##  <a name="set_exception"></a> set_exception 

 將例外狀況傳播至與這個事件相關聯的所有工作。  
  
```
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```  
  
### <a name="parameters"></a>參數  
 `_E`  
 `_Except`  
 `_ExceptionPtr`  
  
### <a name="return-value"></a>傳回值  
  
##  <a name="ctor"></a> task_completion_event 

 建構 `task_completion_event` 物件。  
  
```
task_completion_event();
```  
  
## <a name="see-also"></a>另請參閱  
 [concurrency 命名空間](concurrency-namespace.md)

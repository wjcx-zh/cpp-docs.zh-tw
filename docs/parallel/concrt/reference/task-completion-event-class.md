---
title: task_completion_event 類別
ms.date: 11/04/2016
f1_keywords:
- task_completion_event
- PPLTASKS/concurrency::task_completion_event
- PPLTASKS/concurrency::task_completion_event::task_completion_event
- PPLTASKS/concurrency::task_completion_event::set
- PPLTASKS/concurrency::task_completion_event::set_exception
helpviewer_keywords:
- task_completion_event class
ms.assetid: fb19ed98-f245-48dc-9ba5-487ba879b28a
ms.openlocfilehash: b3e3093cb76df507f8c707e497c9aec75a065057
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142586"
---
# <a name="task_completion_event-class"></a>task_completion_event 類別

`task_completion_event` 類別可讓您延遲執行工作，直到滿足某條件，或是為了回應外部事件而開始工作。

## <a name="syntax"></a>語法

```cpp
template<typename _ResultType>
class task_completion_event;

template<>
class task_completion_event<void>;
```

### <a name="parameters"></a>參數

*_ResultType*<br/>
這個 `task_completion_event` 類別的結果類型。

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[task_completion_event](#ctor)|建構 `task_completion_event` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[set](#set)|已多載。 設定工作完成事件。|
|[set_exception](#set_exception)|已多載。 將例外狀況傳播至與這個事件相關聯的所有工作。|

## <a name="remarks"></a>備註

在需要您建立要完成之工作的情況下，使用從工作完成事件建立的工作，以藉此將其接續排程在未來的某個時間點執行。 `task_completion_event` 必須與您建立的工作具有相同類型，而且在具有該類型值的工作完成事件上呼叫 set 方法，將導致關聯工作完成，並將該值當做結果提供給其接續。

如果永不發出工作完成事件的信號，則當工作完成事件解構時，將會取消從中建立的所有工作。

`task_completion_event` 的行為就像智慧型指標，應該依值傳遞。

## <a name="inheritance-hierarchy"></a>繼承階層

`task_completion_event`

## <a name="requirements"></a>需求

**標頭：** ppltasks.h。h

**命名空間：** concurrency

## <a name="set"></a>設定

設定工作完成事件。

```cpp
bool set(_ResultType _Result) const ;

bool set() const ;
```

### <a name="parameters"></a>參數

*_Result*<br/>
要用來設定此事件的結果。

### <a name="return-value"></a>傳回值

如果成功設定事件，方法會傳回**true** 。 如果已經設定事件，它會傳回**false** 。

### <a name="remarks"></a>備註

如果 `set`有多個或並行呼叫，只有第一個呼叫會成功，而且其結果（如果有的話）會儲存在工作完成事件中。 系統會忽略其餘的集合，且方法會傳回 false。 當您設定工作完成事件時，從該事件建立的所有工作都會立即完成，而且會排程其接續（如果有的話）。 具有**void**以外之 `_ResultType` 的工作完成物件會將值傳遞至其接續。

## <a name="set_exception"></a>set_exception

將例外狀況傳播至與這個事件相關聯的所有工作。

```cpp
template<typename _E>
__declspec(noinline) bool set_exception(_E _Except) const;

__declspec(noinline) bool set_exception(std::exception_ptr _ExceptionPtr) const ;
```

### <a name="parameters"></a>參數

*_E*<br/>
例外狀況型別。

*_Except*<br/>
要設定的例外狀況。

*_ExceptionPtr*<br/>
要設定的例外狀況指標。

### <a name="return-value"></a>傳回值

## <a name="ctor"></a>task_completion_event

建構 `task_completion_event` 物件。

```cpp
task_completion_event();
```

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

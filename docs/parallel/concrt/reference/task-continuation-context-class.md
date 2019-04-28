---
title: task_continuation_context 類別
ms.date: 11/04/2016
f1_keywords:
- task_continuation_context
- PPLTASKS/concurrency::task_continuation_context
- PPLTASKS/concurrency::task_continuation_context::get_current_winrt_context
- PPLTASKS/concurrency::task_continuation_context::use_arbitrary
- PPLTASKS/concurrency::task_continuation_context::use_current
- PPLTASKS/concurrency::task_continuation_context::use_default
- PPLTASKS/concurrency::task_continuation_context::use_synchronous_execution
helpviewer_keywords:
- task_continuation_context class
ms.assetid: 1fb5a76a-3682-45c2-a615-8b6b527741f0
ms.openlocfilehash: 5d7d92fcd1bb00513b9e05030afa56726e87183b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62212853"
---
# <a name="taskcontinuationcontext-class"></a>task_continuation_context 類別

`task_continuation_context` 類別可讓您指定您想要執行接續的位置。 最好只使用這個類別，從 Windows 執行階段應用程式。 對於非 Windows 執行階段應用程式，工作接續的執行內容是由執行階段，而且不進行設定。

## <a name="syntax"></a>語法

```
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_current_winrt_context](#get_current_winrt_context)|傳回表示目前的 winrt 執行緒內容中的工作接續內容物件。|
|[use_arbitrary](#use_arbitrary)|建立可讓執行階段選擇接續執行內容的工作接續內容。|
|[use_current](#use_current)|傳回表示目前執行內容的工作接續內容物件。|
|[use_default](#use_default)|建立預設工作接續內容。|
|[use_synchronous_execution](#use_synchronous_execution)|傳回表示同步執行內容的工作接續內容物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>需求

**標頭：** ppltasks.h

**命名空間：** concurrency

## <a name="get_current_winrt_context"></a> get_current_winrt_context

傳回表示目前的 WinRT 執行緒內容中的工作接續內容物件。

## <a name="syntax"></a>語法

```
static task_continuation_context get_current_winrt_context();
```

## <a name="return-value"></a>傳回值

目前的 Windows 執行階段的執行緒內容。 如果從非 Windows 執行階段內容進行呼叫，則傳回空的 task_continuation_context。

## <a name="remarks"></a>備註

`get_current_winrt_context`方法會擷取呼叫端的 Windows 執行階段的執行緒內容。 非 Windows 執行階段呼叫端，它就會傳回空的內容。

所傳回的值`get_current_winrt_context`可以用來向執行階段，應該執行接續 apartment 模型中的擷取的內容 （STA 或 MTA），無論前項工作是 apartment 感知。 Apartment 感知工作是解除包裝 Windows 執行階段的工作`IAsyncInfo`介面或從這類工作繼承而來的工作。

這個方法很類似`use_current`方法，但它也會提供為原生C++而不需要程式碼C++/CX 延伸模組支援。 它適用於使用進階的使用者撰寫的C++/CX-agnostic 原生和 Windows 執行階段呼叫端的程式庫程式碼。 除非您需要這項功能，我們建議`use_current`方法，它只會提供給C++/CX 用戶端。

##  <a name="use_arbitrary"></a> use_arbitrary

建立可讓執行階段選擇接續執行內容的工作接續內容。

```
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>傳回值

表示任意位置的工作接續內容。

### <a name="remarks"></a>備註

使用這個接續內容時將會在執行階段會選擇，即使前項工作是 apartment 感知內容中執行接續。

`use_arbitrary` 可用來關閉在 STA 中建立 apartment 感知工作的接續預設行為

這個方法只適用於 Windows 執行階段應用程式的選項。

##  <a name="use_current"></a> use_current

傳回表示目前執行內容的工作接續內容物件。

```
static task_continuation_context use_current();
```

### <a name="return-value"></a>傳回值

目前執行內容。

### <a name="remarks"></a>備註

這個方法會擷取呼叫端的 Windows 執行階段內容，以便在正確的 apartment 中執行接續。

所傳回的值`use_current`可以用來向執行階段，不論前項工作為 apartment 感知擷取的內容 （STA 或 MTA） 中執行接續。 Apartment 感知工作是解除包裝 Windows 執行階段的工作`IAsyncInfo`介面或從這類工作繼承而來的工作。

這個方法只適用於 Windows 執行階段應用程式的選項。

##  <a name="use_default"></a> use_default

建立預設工作接續內容。

```
static task_continuation_context use_default();
```

### <a name="return-value"></a>傳回值

預設接續內容。

### <a name="remarks"></a>備註

如果您沒有指定接續內容呼叫時，會使用預設內容`then`方法。 在 Windows 應用程式適用於 Windows 7 及之前的版本，以及桌面應用程式在 Windows 8 和更新版本，執行階段會判斷工作接續將執行的位置。 不過，在 Windows 執行階段應用程式中，apartment 感知工作的接續的預設接續內容是 apartment 其中`then`叫用。

Apartment 感知工作是解除包裝 Windows 執行階段的工作`IAsyncInfo`介面或從這類工作繼承而來的工作。 因此，如果您排程在 Windows 執行階段 STA apartment 感知工作的接續時，接續會執行在該 sta。

非 apartment 感知工作的接續將執行階段選擇的內容中執行。

## <a name="use_synchronous_execution"></a> task_continuation_context::use_synchronous_execution

傳回表示同步執行內容的工作接續內容物件。

## <a name="syntax"></a>語法

```
static task_continuation_context use_synchronous_execution();
```

## <a name="return-value"></a>傳回值

同步的執行內容。

## <a name="remarks"></a>備註

`use_synchronous_execution`方法會強制設為於內容，導致其前項工作的完成同步執行接續工作。

如果附加接續時前項工作已完成，接續會以同步方式執行附加接續內容。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

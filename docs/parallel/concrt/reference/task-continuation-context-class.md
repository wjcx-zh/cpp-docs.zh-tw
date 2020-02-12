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
ms.openlocfilehash: ae8ac425f035839cdddc0b19f4f40d3b6369202a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142580"
---
# <a name="task_continuation_context-class"></a>task_continuation_context 類別

`task_continuation_context` 類別可讓您指定您想要執行接續的位置。 這僅適用于從 Windows 執行階段應用程式使用此類別。 針對非 Windows 執行階段的應用程式，工作接續的執行內容是由執行時間所決定，而且無法設定。

## <a name="syntax"></a>語法

```cpp
class task_continuation_context : public details::_ContextCallback;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[get_current_winrt_coNtext](#get_current_winrt_context)|傳回表示目前 winrt 執行緒內容的 task 接續內容物件。|
|[use_arbitrary](#use_arbitrary)|建立可讓執行階段選擇接續執行內容的工作接續內容。|
|[use_current](#use_current)|傳回表示目前執行內容的工作接續內容物件。|
|[use_default](#use_default)|建立預設工作接續內容。|
|[use_synchronous_execution](#use_synchronous_execution)|傳回表示同步執行內容的工作接續內容物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`_ContextCallback`

`task_continuation_context`

## <a name="requirements"></a>需求

**標頭：** ppltasks.h。h

**命名空間：** concurrency

## <a name="get_current_winrt_context"></a>get_current_winrt_coNtext

傳回表示目前 WinRT 執行緒內容的 task 接續內容物件。

### <a name="syntax"></a>語法

```cpp
static task_continuation_context get_current_winrt_context();
```

### <a name="return-value"></a>傳回值

目前的 Windows 執行階段執行緒內容。 如果從非 Windows 執行階段內容呼叫，則會傳回空的 task_continuation_coNtext。

### <a name="remarks"></a>備註

`get_current_winrt_context` 方法會捕捉呼叫者的 Windows 執行階段執行緒內容。 它會將空的內容傳回給非 Windows 執行階段的呼叫端。

`get_current_winrt_context` 所傳回的值，可以用來向運行時程表示接續應在已捕捉內容的單元模型（STA vs MTA）中執行，不論 antecedent 工作是否為「單元感知」。 「單元感知」工作是將 Windows 執行階段的 `IAsyncInfo` 介面解除包裝，或從這類工作衍生的工作。

這個方法與 `use_current` 方法類似，但它也適用于沒有C++ C++/cx 延伸模組支援的機器碼。 這適用于將/CX-agnostic 程式庫程式碼C++同時寫入原生和 Windows 執行階段呼叫端的先進使用者。 除非您需要此功能，否則建議使用 `use_current` 方法，這僅適用于C++/cx 用戶端。

## <a name="use_arbitrary"></a>use_arbitrary

建立可讓執行階段選擇接續執行內容的工作接續內容。

### <a name="syntax"></a>語法

```cpp
static task_continuation_context use_arbitrary();
```

### <a name="return-value"></a>傳回值

表示任意位置的工作接續內容。

### <a name="remarks"></a>備註

使用此接續內容時，接續將會在執行時間所選擇的內容中執行，即使 antecedent 工作是「單元感知」也一樣。

`use_arbitrary` 可用來關閉在 STA 中建立的公寓感知工作上接續的預設行為。

這個方法僅適用于 Windows 執行階段應用程式。

## <a name="use_current"></a>use_current

傳回表示目前執行內容的工作接續內容物件。

```cpp
static task_continuation_context use_current();
```

### <a name="return-value"></a>傳回值

目前執行內容。

### <a name="remarks"></a>備註

這個方法會捕捉呼叫者的 Windows 執行階段內容，以便在正確的單元中執行接續。

`use_current` 所傳回的值，可以用來向運行時程表示接續應在已捕捉的內容（STA vs MTA）中執行，而不論 antecedent 工作是否為單元感知。 「單元感知」工作是將 Windows 執行階段的 `IAsyncInfo` 介面解除包裝，或從這類工作衍生的工作。

這個方法僅適用于 Windows 執行階段應用程式。

## <a name="use_default"></a>use_default

建立預設工作接續內容。

```cpp
static task_continuation_context use_default();
```

### <a name="return-value"></a>傳回值

預設接續內容。

### <a name="remarks"></a>備註

如果您在呼叫 `then` 方法時未指定接續內容，則會使用預設內容。 在適用于 Windows 7 和更新版本的 Windows 應用程式中，以及 Windows 8 和更新版本上的桌面應用程式中，執行時間會決定工作接續的執行位置。 不過，在 Windows 執行階段應用程式中，在「單元感知」工作上接續的預設接續內容，就是叫用 `then` 的所在所在的單元。

「單元感知」工作是將 Windows 執行階段的 `IAsyncInfo` 介面解除包裝，或從這類工作衍生的工作。 因此，如果您在 Windows 執行階段 STA 中的「單元感知」工作上排程接續，則會在該 STA 中執行接續。

非範圍感知工作上的接續將會在執行時間所選擇的內容中執行。

## <a name="use_synchronous_execution"></a>task_continuation_coNtext：： use_synchronous_execution

傳回表示同步執行內容的工作接續內容物件。

### <a name="syntax"></a>語法

```cpp
static task_continuation_context use_synchronous_execution();
```

### <a name="return-value"></a>傳回值

同步執行內容。

### <a name="remarks"></a>備註

`use_synchronous_execution` 方法會強制接續工作在內容上以同步方式執行，導致其先前的工作完成。

如果附加接續時，antecedent 工作已經完成，接續會以同步方式在附加接續的內容上執行。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)

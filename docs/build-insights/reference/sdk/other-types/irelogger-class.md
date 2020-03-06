---
title: IRelogger 類別
description: C++ BUILD Insights SDK IRelogger 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332443"
---
# <a name="irelogger-class"></a>IRelogger 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`IRelogger` 類別提供用來 relogging Windows 事件追蹤（ETW）追蹤的介面。 它會與[MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)和[MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)函數搭配使用。 使用 `IRelogger` 做為基類，以建立您自己的 relogger，其可以是 relogger 群組的一部分。

## <a name="syntax"></a>語法

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>備註

不會覆寫之所有函式的預設傳回值為 `AnalysisControl::CONTINUE`。 如需詳細資訊，請參閱[AnalysisControl](analysis-control-enum-class.md)。

## <a name="members"></a>成員

### <a name="destructor"></a>解構函式

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

終結 IRelogger 類別。

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

此函式會在 relogging 階段開始之前呼叫。

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

此函式會在 relogging 階段開始時呼叫。

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-end-relogging"></a>OnEndRelogging

此函式會在 relogging 階段結束後呼叫。

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

此函式會在 relogging 階段結束時呼叫。

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

處理簡單事件時，會呼叫這個函式。

### <a name="parameters"></a>參數

*eventStack*\
這個簡單事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

當處理活動啟動事件時，會呼叫這個函式。

### <a name="parameters"></a>參數

*eventStack*\
此活動開始事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-stop-activity"></a>OnStopActivity

當處理活動停止事件時，會呼叫這個函式。

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>參數

*eventStack*\
此活動停止事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

此函式會在每次分析或 relogging 階段開始時呼叫一次。

### <a name="parameters"></a>參數

*traceInfo*\
[TraceInfo](../cpp-event-data-types/trace-info.md)物件，其中包含有關所耗用之追蹤的實用屬性。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

::: moniker-end

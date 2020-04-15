---
title: IRelogger 類別
description: C++生成見解 SDK IRelogger 類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329148"
---
# <a name="irelogger-class"></a>IRelogger 類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`IRelogger`類提供了一個介面,用於重新記錄 Windows (ETW) 跟蹤的事件追蹤。 它與[MakeDynamic ReloggerGroup](../functions/make-dynamic-relogger-group.md)和[使靜態重新記錄組](../functions/make-static-analyzer-group.md)功能一起使用。 用作`IRelogger`基類,創建自己的重新記錄器,該重新記錄器可以是重新記錄組的一部分。

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

未重寫的所有函數的預設傳回值`AnalysisControl::CONTINUE`為 。 有關詳細資訊,請參閱[分析控制](analysis-control-enum-class.md)。

## <a name="members"></a>成員

### <a name="destructor"></a>解構函式

[*IRelogger](#irelogger-destructor)

### <a name="functions"></a>函式

[開始重新記錄](#on-begin-relogging)\
[在「開始記錄」Pass](#on-begin-relogging-pass)\
[結束重新記錄](#on-end-relogging)\
[結束重新紀錄頻道](#on-end-relogging-pass)\
[在Simple事件上](#on-simple-event)\
[啟動活動](#on-start-activity)\
[停止活動](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>*IRelogger

銷毀IRelogger類。

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>開始重新記錄

在重新記錄記錄傳遞開始之前呼叫此功能。

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>在「開始記錄」Pass

此函數在重新記錄通道的開頭調用。

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>結束重新記錄

重新記錄傳遞結束後調用此功能。

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>結束重新紀錄頻道

此函數在重新記錄通道結束時調用。

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>在Simple事件上

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

正在處理簡單事件時調用此函數。

### <a name="parameters"></a>參數

*事件堆疊*\
此簡單事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onstartactivity"></a><a name="on-start-activity"></a>啟動活動

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

正在處理活動啟動事件時調用此函數。

### <a name="parameters"></a>參數

*事件堆疊*\
此活動啟動事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>停止活動

正在處理活動停止事件時調用此函數。

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>參數

*事件堆疊*\
此活動停止事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

此函數在每個分析或重新記錄傳遞開始時調用一次。

### <a name="parameters"></a>參數

*追蹤資訊*\
包含有關要消耗的跟蹤的有用屬性的[TraceInfo](../cpp-event-data-types/trace-info.md)物件。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

::: moniker-end

---
title: IAnalyzer 類別
description: C++生成見解 SDK IAnalyzer 類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329178"
---
# <a name="ianalyzer-class"></a>IAnalyzer 類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`IAnalyzer`類提供了一個用於分析 Windows (ETW) 追蹤的事件跟蹤的介面。 它與[製作動態分析器組](../functions/make-dynamic-analyzer-group.md)、[使動態重新記錄組](../functions/make-dynamic-relogger-group.md)、[使靜態分析器組](../functions/make-dynamic-analyzer-group.md)和[使靜態重新記錄組](../functions/make-static-analyzer-group.md)功能一起使用。 用作`IAnalyzer`基類,創建自己的分析器,該分析器可以是分析器或重新記錄組的一部分。

## <a name="syntax"></a>語法

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>備註

派生自`IAnalyzer`的類可用作分析器和重新記錄器。 當用作重新記錄器時,重新記錄特定的函數重定向到其分析器等效項。 相反,情況並非如此:派生自`IRelogger`的類不能用作分析器。 在重新記錄組中使用分析器是一種常見的模式。 當放置在重新記錄組的早期位置時,分析儀可以預先計算資訊,並使其可用於以後位置的重新記錄。

未重寫的所有函數的預設傳回值`AnalysisControl::CONTINUE`為 。 有關詳細資訊,請參閱[分析控制](analysis-control-enum-class.md)。

## <a name="members"></a>成員

除了`IRelogger`介面`IAnalyzer`中的[OnTraceInfo](irelogger-class.md#on-trace-info)成員外,該類還包含以下成員:

### <a name="destructor"></a>解構函式

[*IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>函式

[上開始分析](#on-begin-analysis)\
[OnBegin 分析通行證](#on-begin-analysis-pass)\
[開始重新記錄](#on-begin-relogging)\
[在「開始記錄」Pass](#on-begin-relogging-pass)\
[結束剖析](#on-end-analysis)\
[上端分析通](#on-end-analysis-pass)\
[結束重新記錄](#on-end-relogging)\
[結束重新紀錄頻道](#on-end-relogging-pass)\
[在Simple事件上](#on-simple-event)\
[啟動活動](#on-start-activity)\
[停止活動](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>*IAnalyzer

銷毀IAnalyzer類。

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>上開始分析

對於分析器組一部分的分析器,在第一次分析傳遞開始之前調用此函數。 對於重新記錄組中的分析器部分,在重新記錄傳遞開始之前調用此功能。 對於同一重新記錄作業階段的分析器和重新記錄組部分的分析器,在第一次分析傳遞開始之前,將調用此函數兩次。

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBegin 分析通行證

對於分析器組一部分的分析器,在每次分析傳遞開始時調用此函數。 對於重新記錄組中的分析器,此函數在重新記錄器傳遞的開頭調用。 對於同一重新記錄工作階段的分析器和重新記錄組部分的分析器,在每次分析通過開始時和重新記錄器傳遞開始時調用此功能。

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>開始重新記錄

```cpp
AnalysisControl OnBeginRelogging() final;
```

無法重寫此功能。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 此函數將呼叫重定到[OnBeginAnalysis](#on-begin-analysis)。

### <a name="return-value"></a>傳回值

[OnBegin 分析](#on-begin-analysis)調用的結果。

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>在「開始記錄」Pass

無法重寫此功能。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 此函數會呼叫重定到[OnBegin 分析 Pass](#on-begin-analysis-pass)。

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>傳回值

[OnBegin分析通](#on-begin-analysis-pass)電話的結果。

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>結束剖析

對於分析器組一部分的分析器,在最後一次分析傳遞結束後調用此功能。 對於作為重新記錄組一部分的分析儀,在重新記錄傳遞結束後調用此功能。 對於屬於同一重新紀錄紀錄工作階段的分析器和重新記錄組一部分的分析器,此函數呼叫兩次:

1. 所有分析通過結束后和重新記錄通過開始之前,
1. 重新記錄通過結束後。

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>上端分析通

對於分析器組一部分的分析器,每次分析傳遞結束時都會調用此函數。 對於重新記錄組中的分析器,此函數在重新記錄器通過結束時調用。 對於同一重新記錄工作階段的分析器和重新記錄組部分的分析器,在每次分析通過結束時和重新記錄器通過結束時調用此功能。

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>結束重新記錄

無法重寫此功能。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 此函數會呼叫重定到[OnEndAnalysis](#on-end-analysis)。

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>傳回值

[OnEnd 分析](#on-end-analysis)調用的結果。

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>結束重新紀錄頻道

無法重寫此功能。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 此函數會呼叫重定到[OnEndAnalysisPass](#on-end-analysis-pass)。

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>傳回值

[OnendAnalysisPass](#on-end-analysis-pass)調用的結果。

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>在Simple事件上

正在處理簡單事件時調用此函數。 無法重寫此函數的第二個版本。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 對版本 2 的所有調用都重定向到版本 1。

### <a name="version-1"></a>第 1 版

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>第 2 版

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>參數

*事件堆疊*\
此簡單事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

*重新登入工作階段*\
不使用這個參數。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onstartactivity"></a><a name="on-start-activity"></a>啟動活動

正在處理活動啟動事件時調用此函數。 無法重寫此函數的第二個版本。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 對版本 2 的所有調用都重定向到版本 1。

### <a name="version-1"></a>第 1 版

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>第 2 版

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>參數

*事件堆疊*\
此活動啟動事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

*重新登入工作階段*\
不使用這個參數。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>停止活動

正在處理活動停止事件時調用此函數。 無法重寫此函數的第二個版本。 當分析器是重新記錄組的一部分時,C++生成見解 SDK 調用它。 對版本 2 的所有調用都重定向到版本 1。

### <a name="version-1"></a>第 1 版

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>第 2 版

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>參數

*事件堆疊*\
此活動停止事件的事件堆疊。 有關事件堆疊的詳細資訊,請參閱[事件](../event-table.md)。

*重新登入工作階段*\
不使用這個參數。

### <a name="return-value"></a>傳回值

分析[控制](analysis-control-enum-class.md)代碼,描述接下來會發生什麼。

::: moniker-end

---
title: IAnalyzer 類別
description: C++ BUILD Insights SDK IAnalyzer 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332450"
---
# <a name="ianalyzer-class"></a>IAnalyzer 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`IAnalyzer` 類別提供分析 Windows 事件追蹤（ETW）追蹤的介面。 它會與[MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)、 [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md)、 [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)和[MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md)函數搭配使用。 使用 `IAnalyzer` 做為基類，以建立您自己的分析器，它可以是分析器或 relogger 群組的一部分。

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

衍生自 `IAnalyzer` 的類別可以同時當做分析器和 reloggers 使用。 當做 reloggers 使用時，relogger 特有的函式會重新導向至其分析器的對應項。 反向不是 true：衍生自 `IRelogger` 的類別無法當做分析器使用。 在 relogger 群組中流量分析器是常見的模式。 當放在 relogger 群組的早期位置時，分析器可以預先計算資訊，並使其可在稍後的位置 reloggers。

不會覆寫之所有函式的預設傳回值為 `AnalysisControl::CONTINUE`。 如需詳細資訊，請參閱[AnalysisControl](analysis-control-enum-class.md)。

## <a name="members"></a>成員

除了 `IRelogger` 介面的[OnTraceInfo](irelogger-class.md#on-trace-info)成員之外，`IAnalyzer` 類別還包含下列成員：

### <a name="destructor"></a>解構函式

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

終結 IAnalyzer 類別。

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

對於分析器群組的分析器部分，會在第一次分析階段開始之前呼叫此函式。 對於 relogger 群組的分析器部分，會在 relogging 階段開始之前呼叫此函式。 針對相同 relogging 會話的分析器和 relogger 群組中的分析器，在第一次分析階段開始之前，會呼叫此函式兩次。

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

對於分析器群組的分析器部分，會在每個分析階段開始時呼叫此函式。 對於 relogger 群組的分析器部分，此函式會在 relogger 階段開始時呼叫。 對於相同 relogging 會話的分析器和 relogger 群組中的分析器，此函式會在每次分析階段開始時，以及在 relogger 階段開始時呼叫。

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

無法覆寫此函數。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 此函式會將呼叫重新導向至[OnBeginAnalysis](#on-begin-analysis)。

### <a name="return-value"></a>傳回值

[OnBeginAnalysis](#on-begin-analysis)呼叫的結果。

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

無法覆寫此函數。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 此函式會將呼叫重新導向至[OnBeginAnalysisPass](#on-begin-analysis-pass)。

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>傳回值

[OnBeginAnalysisPass](#on-begin-analysis-pass)呼叫的結果。

## <a name="on-end-analysis"></a>OnEndAnalysis

針對屬於分析器群組一部分的分析器，在最後一個分析行程結束之後，會呼叫此函式。 針對屬於 relogger 群組一部分的分析器，會在 relogging pass 結束後呼叫此函式。 對於同時屬於相同 relogging 會話之分析器和 relogger 群組的分析器，會呼叫此函式兩次：

1. 當所有分析通過結束之後，開始 relogging 階段之前，和
1. relogging pass 結束之後。

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

對於分析器群組的分析器部分，會在每個分析階段結束時呼叫此函式。 對於 relogger 群組的分析器部分，此函式會在 relogger 階段結束時呼叫。 對於相同 relogging 會話的分析器和 relogger 群組中的分析器，此函式會在每次分析階段結束時呼叫，並在 relogger 階段結束時呼叫。

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-end-relogging"></a>OnEndRelogging

無法覆寫此函數。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 此函式會將呼叫重新導向至[OnEndAnalysis](#on-end-analysis)。

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>傳回值

[OnEndAnalysis](#on-end-analysis)呼叫的結果。

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

無法覆寫此函數。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 此函式會將呼叫重新導向至[OnEndAnalysisPass](#on-end-analysis-pass)。

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>傳回值

[OnEndAnalysisPass](#on-end-analysis-pass)呼叫的結果。

## <a name="on-simple-event"></a>OnSimpleEvent

處理簡單事件時，會呼叫這個函式。 無法覆寫此函式的第二個版本。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 第2版的所有呼叫都會重新導向至第1版。

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

*eventStack*\
這個簡單事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

*relogSession*\
不使用這個參數。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-start-activity"></a>OnStartActivity

當處理活動啟動事件時，會呼叫這個函式。 無法覆寫此函式的第二個版本。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 第2版的所有呼叫都會重新導向至第1版。

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

*eventStack*\
此活動開始事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

*relogSession*\
不使用這個參數。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

## <a name="on-stop-activity"></a>OnStopActivity

當處理活動停止事件時，會呼叫這個函式。 無法覆寫此函式的第二個版本。 當分析器是 relogger 群組C++的一部分時，BUILD Insights SDK 會呼叫它。 第2版的所有呼叫都會重新導向至第1版。

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

*eventStack*\
此活動停止事件的事件堆疊。 如需事件堆疊的詳細資訊，請參閱[事件](../event-table.md)。

*relogSession*\
不使用這個參數。

### <a name="return-value"></a>傳回值

描述接下來應該發生什麼情況的[AnalysisControl](analysis-control-enum-class.md)程式碼。

::: moniker-end

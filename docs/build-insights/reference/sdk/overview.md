---
title: C++建構
description: 可視化工作室C++構建見解 SDK 的概述。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 126abb0d039227eb269500966d46ef0a729763ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323267"
---
# <a name="c-build-insights-sdk"></a>C++建構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

C++構建見解 SDK 是 API 的集合,允許您在C++構建見解平台的基礎上創建個人化工具。 本頁提供高級概述,以説明您入門。

## <a name="obtaining-the-sdk"></a>取得 SDK

您可以按照以下步驟下載C++生成見解 SDK 作為 NuGet 套件:

1. 從 Visual Studio 2017 及以上,創建新C++專案。
1. 在 **「解決方案資源管理器」** 窗格中,右鍵單擊專案。
1. 從上下文選單中選擇 **「管理 NuGet 包**」。
1. 在右上角,選擇**nuget.org**包源。
1. 搜索最新版本的 Microsoft.Cpp.Build Insights 包。
1. 選擇 **「安裝**」 。
1. 接受許可證。

請繼續閱讀,瞭解有關 SDK 周圍的一般概念的資訊。 您還可以造訪正式[C++生成見解範例 GitHub 儲存函式庫](https://github.com/microsoft/cpp-build-insights-samples),以查看使用 SDK 的實際 C++應用程式的範例。

## <a name="collecting-a-trace"></a>收集追蹤

使用C++生成見解 SDK 分析來自 MSVC 工具鏈的事件需要您首先收集跟蹤。 SDK 利用 Windows 事件追蹤 (ETW) 作為基礎追蹤技術。 收集追蹤可透過兩種方式完成:

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法 1:在 2019 年及以上視覺工作室中使用 vcperf

1. 打開 VS 2019 的提升 x64 本機工具命令提示。
1. 執行下列命令：`vcperf /start MySessionName`
1. 建置您的專案。
1. 執行下列命令：`vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > 使用`/stopnoanalyze`vcperf 停止追蹤時,請使用該命令。 不能使用C++生成見解 SDK 來`/stop`分析常規 命令停止的跟蹤。

### <a name="method-2-programmatically"></a>方法 2:以程式設計方式

使用這些C++生成見解 SDK 跟蹤收集函數中的任何一個以程式設計方式啟動和停止追蹤。 **執行這些函數調用的程序必須具有管理許可權。** 只有啟動和停止跟蹤函數需要管理許可權。 C++生成見解 SDK 中的所有其他功能都可以在沒有這些功能的情況下執行。

### <a name="sdk-functions-related-to-trace-collection"></a>與追蹤收集相關的 SDK 函式

| 功能 | C++ API | C API |
|--|--|--|
| 啟動追蹤 | [開始追蹤工作階段](functions/start-tracing-session.md) | [開始追蹤工作階段A](functions/start-tracing-session-a.md)<br />[開始追蹤工作階段W](functions/start-tracing-session-w.md) |
| 停止追蹤 | [停止追蹤工作階段](functions/stop-tracing-session.md) | [停止追蹤工作階段A](functions/stop-tracing-session-a.md)<br />[停止追蹤工作階段W](functions/stop-tracing-session-w.md) |
| 停止追蹤與<br />立即分析結果 | [停止並分析追蹤工作階段](functions/stop-and-analyze-tracing-session.md) | [停止並分析追蹤工作階段A](functions/stop-and-analyze-tracing-session-a.md)<br />[停止並分析追蹤工作階段](functions/stop-and-analyze-tracing-session-w.md) |
| 停止追蹤與<br />立即重新紀錄結果 | [停止並重新記錄追蹤工作階段](functions/stop-and-relog-tracing-session.md) | [停止並重新登入追蹤工作階段A](functions/stop-and-relog-tracing-session-a.md)<br />[停止並重新記錄追蹤工作階段W](functions/stop-and-relog-tracing-session-w.md) |

以下各節將介紹如何配置分析或重新記錄會話。 組合功能功能(如[StopAndAnalyze 跟蹤會話](functions/stop-and-analyze-tracing-session.md))是必需的。

## <a name="consuming-a-trace"></a>使用追蹤

獲得 ETW 追蹤後,請使用 C++生成見解 SDK 將其解壓縮。 SDK 以允許您快速開發工具的格式為您提供事件。 我們不建議您不使用 SDK 使用原始 ETW 追蹤。 MSVC 使用的事件格式沒有記錄,經過最佳化以擴展到大型生成,而且很難理解。 此外,C++生成見解 SDK API 是穩定的,而原始 ETW 跟蹤格式可能會更改,恕不另行通知。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>與追蹤消耗相關的 SDK 型態與函數

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 設定事件回檔 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++生成見解 SDK 通過回調功能提供事件。 在C++,通過創建繼承IAnalyzer或IRelogger介面的分析器或重新記錄器類來實現回調函數。 在 C 中,在全域函數中實現回調,並在ANALYSIS_CALLBACKS或RELOG_CALLBACKS結構中提供指向它們的指標。 |
| 建築組 | [靜態分析器群組](functions/make-static-analyzer-group.md)<br />[將靜態重新記錄群組](functions/make-static-relogger-group.md)<br />[製作動態分析器群組](functions/make-dynamic-analyzer-group.md)<br />[將動態重新記錄群組](functions/make-dynamic-relogger-group.md) |  | C++ API 提供幫助器功能和類型,將多個分析器和重新記錄物件組合在一起。 組是將複雜分析劃分為更簡單步驟的巧妙方法。 [vcperf](https://github.com/microsoft/vcperf)是以這種方式組織的。 |
| 剖析或重新記錄 | [分析](functions/analyze.md)<br />[重新登入](functions/relog.md) | [分析A](functions/analyze-a.md)<br />[分析W](functions/analyze-w.md)<br />[雷洛加](functions/relog-a.md)<br />[雷洛格瓦](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>剖析並重新記錄

使用跟蹤是通過分析會話或重新記錄會話完成的。

使用常規分析適用於大多數方案。 此方法使您能夠靈活地選擇輸出格式:`printf`文本、xml、JSON、資料庫、REST 調用等。

重新記錄用於需要生成 ETW 輸出檔的特殊用途分析。 使用重新登錄,您可以將C++生成見解事件轉換為您自己的 ETW 事件格式。 適當使用重新日誌記錄是C++構建見解數據與現有的 ETW 工具和基礎結構挂鉤。 例如[,vcperf](https://github.com/microsoft/vcperf)利用重新記錄介面。 這是因為它必須生成 Windows 性能分析器(ETW 工具)可以理解的數據。 如果您計劃使用重新記錄介面,則需要事先瞭解 ETW 的工作原理。

### <a name="creating-analyzer-groups"></a>建立分析器群組

瞭解如何創建組非常重要。 下面是一個示例,演示如何創建列印*Hello,世界的分析*器組! 對於它接收的每個活動開始事件。

```cpp
using namespace Microsoft::Cpp::BuildInsights;

class Hello : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "Hello, " << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

class World : public IAnalyzer
{
public:
    AnalysisControl OnStartActivity(
        const EventStack& eventStack) override
    {
        std::cout << "world!" << std::endl;
        return AnalysisControl::CONTINUE;
    }
};

int main()
{
    Hello hello;
    World world;

    // Let's make Hello the first analyzer in the group
    // so that it receives events and prints "Hello, "
    // first.
    auto group = MakeStaticAnalyzerGroup(&hello, &world);

    unsigned numberOfAnalysisPasses = 1;

    // Calling this function initiates the analysis and
    // forwards all events from "inputTrace.etl" to my analyzer
    // group.
    Analyze("inputTrace.etl", numberOfAnalysisPasses, group);

    return 0;
}
```

## <a name="using-events"></a>使用事件

### <a name="sdk-types-and-functions-related-to-events"></a>與事件相關的 SDK 類型與函式

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 符合與篩選事件 | [符合事件堆疊成員函數](functions/match-event-stack-in-member-function.md)<br />[符合事件堆疊](functions/match-event-stack.md)<br />[符合事件成員函數](functions/match-event-in-member-function.md)<br />[符合事件](functions/match-event.md) |  | C++ API 提供了功能,便於從跟蹤中提取您關心的事件。 使用 C API 時,必須手動完成此篩選。 |
| 事件資料類型 | [活動](cpp-event-data-types/activity.md)<br />[後端通行證](cpp-event-data-types/back-end-pass.md)<br />[自下而上](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[代碼產生](cpp-event-data-types/code-generation.md)<br />[命令列](cpp-event-data-types/command-line.md)<br />[編譯器](cpp-event-data-types/compiler.md)<br />[編譯器通行證](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[事件](cpp-event-data-types/event.md)<br />[活動群組](cpp-event-data-types/event-group.md)<br />[事件堆疊](cpp-event-data-types/event-stack.md)<br />[可執行影像輸出](cpp-event-data-types/executable-image-output.md)<br />[Exp輸出](cpp-event-data-types/exp-output.md)<br />[檔案輸入](cpp-event-data-types/file-input.md)<br />[檔案輸出](cpp-event-data-types/file-output.md)<br />[力因內](cpp-event-data-types/force-inlinee.md)<br />[前端檔案](cpp-event-data-types/front-end-file.md)<br />[前端檔案群組](cpp-event-data-types/front-end-file-group.md)<br />[前端通票](cpp-event-data-types/front-end-pass.md)<br />[函數](cpp-event-data-types/function.md)<br />[ImpLib 輸出](cpp-event-data-types/imp-lib-output.md)<br />[引動過程](cpp-event-data-types/invocation.md)<br />[呼叫群組](cpp-event-data-types/invocation-group.md)<br />[Lib輸出](cpp-event-data-types/lib-output.md)<br />[連結器](cpp-event-data-types/linker.md)<br />[連結器組](cpp-event-data-types/linker-group.md)<br />[連結器Pass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[Obj輸出](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[通行證1](cpp-event-data-types/pass1.md)<br />[通行證2](cpp-event-data-types/pass2.md)<br />[前LTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[簡單事件](cpp-event-data-types/simple-event.md)<br />[符號名稱](cpp-event-data-types/symbol-name.md)<br />[樣本即時性](cpp-event-data-types/template-instantiation.md)<br />[樣本即時群組](cpp-event-data-types/template-instantiation-group.md)<br />[執行緒](cpp-event-data-types/thread.md)<br />[自上而下](cpp-event-data-types/top-down.md)<br />[追蹤資訊](cpp-event-data-types/trace-info.md)<br />[整個程式分析](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>活動及簡單活動

作用分式:*活動與**簡單活動*。 活動是及時進行的過程,有開始和結束。 簡單的事件是準時發生的事件,沒有持續時間。 使用C++生成見解 SDK 分析 MSVC 追蹤時,當活動啟動和停止時,您將收到單獨的事件。 當發生簡單事件時,您只能收到一個事件。

### <a name="parent-child-relationships"></a>父子關係

活動和簡單事件通過父子關係彼此相關。 活動或簡單事件的父級是發生活動時包含的活動。 例如,編譯源檔時,編譯器必須分析該檔,然後生成代碼。 解析和代碼生成活動都是編譯器活動的子級。

簡單的事件沒有持續時間,所以裡面沒有其他事件。 因此,他們從來沒有孩子。

[事件表中](event-table.md)指示每個活動和簡單事件的父子關係。 在使用C++生成見解事件時,瞭解這些關係非常重要。 您通常必須依靠它們來瞭解事件的完整上下文。

### <a name="properties"></a>屬性

所有事件都具有以下屬性:

| 屬性 | 描述 |
|--|--|
| 型態識別碼 | 唯一標識事件類型的數位。 |
| 實體識別碼 | 唯一標識跟蹤中事件的數位。 如果跟蹤中發生兩個相同類型的事件,則兩者都將獲得唯一的實例標識符。 |
| 開始時間 | 活動開始的時間或發生簡單事件的時間。 |
| 流程識別碼 | 標識事件發生過程的數位。 |
| 執行緒識別碼 | 標識事件發生的線程的數位。 |
| 處理器索引 | 一個從零開始索引,指示事件由哪個邏輯處理器發出。 |
| 事件名稱 | 描述事件類型的字串。 |

簡單事件以外的所有活動也具有以下屬性:

| 屬性 | 描述 |
|--|--|
| 停止時間 | 活動停止的時間。 |
| 獨家持續時間 | 在活動中花費的時間,不包括在其子活動中花費的時間。 |
| CPU 時間 | CPU 在附加到活動的線程中執行代碼的時間。 它不包括附加到活動線程睡眠的時間。 |
| 專屬 CPU 時間 | 與 CPU 時間相同,但不包括子活動花費的 CPU 時間。 |
| 鐘點時間責任 | 活動對總掛鐘時間的貢獻。 鐘點時間責任考慮到活動之間的並行性。 例如,假設兩個不相關的活動並行運行。 兩者都有 10 秒的持續時間,並且完全相同的開始和停止時間。 在這種情況下,Build Insights 會同時分配 5 秒的掛鐘時間責任。 相反,如果這些活動一個接一個地運行,沒有重疊,則它們都分配了 10 秒的掛鐘時間責任。 |
| 獨家掛鐘時間責任 | 與掛鐘時間責任相同,但不包括兒童活動的掛鐘時間責任。 |

某些事件具有超出上述屬性的屬性。 在這種情況下,這些附加屬性列在[事件表中](event-table.md)。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>使用C++產生見解 SDK 提供的事件

#### <a name="the-event-stack"></a>事件堆疊

每當C++生成見解 SDK 為您提供事件時,它都會以堆疊的形式出現。 堆疊中的最後一個條目是當前事件,其之前的條目是其父層次結構。 例如[,LTCG](event-table.md#ltcg)啟動和停止事件發生在連結器的通過 1 期間。 在這種情況下,您收到的堆疊包含\[[:LINKER、PASS1](event-table.md#linker)、LTCG [ ](event-table.md#pass1) \]。 父層次結構很方便,因為您可以將事件追溯到其根。 如果上述 LTCG 活動速度較慢,您可以立即瞭解涉及哪個連結器調用。

#### <a name="matching-events-and-event-stacks"></a>符合事件與事件堆疊

C++生成見解 SDK 為您提供跟蹤中的每個事件,但大多數時候您只關心其中的子集。 在某些情況下,您可能只關心*事件堆疊的*子集。 SDK 提供了説明您快速提取所需事件或事件堆疊以及拒絕不需要的事件或事件堆疊的設施。 它透過以下符合功能完成:

|  |  |
|--|--|
| [符合事件](functions/match-event.md) | 如果事件與指定類型之一匹配,請保留該事件。 將匹配的事件轉發到 lambda 或其他可調用類型。 此函數不考慮事件的父層次結構。 |
| [符合事件成員函數](functions/match-event-in-member-function.md) | 如果事件與成員函數參數中指定的類型匹配,請保留該事件。 將匹配的事件轉發到成員函數。 此函數不考慮事件的父層次結構。 |
| [符合事件堆疊](functions/match-event-stack.md) | 如果事件及其父層次結構都與指定的類型匹配,則保留事件。 將事件和匹配的父層次結構事件轉發到 lambda 或其他可調用類型。 |
| [符合事件堆疊成員函數](functions/match-event-stack-in-member-function.md) | 如果事件及其父層次結構與成員函數參數清單中指定的類型匹配,則保留事件。 將事件和匹配的父層次結構事件轉發到成員函數。 |

事件堆疊匹配函數,`MatchEventStack`如在描述父層次結構時允許間隙匹配。 例如,你可以說你對\[[LINKER,LTCG](event-table.md#linker)[LTCG](event-table.md#ltcg)\]堆疊感興趣。 它還匹配\[LINKER,PASS1,LTCG[PASS1](event-table.md#pass1)\]堆疊。 指定的最後一種類型必須是要匹配的事件類型,並且不是父層次結構的一部分。

#### <a name="capture-classes"></a>捕獲類

使用`Match*`函數需要指定要匹配的類型。 這些類型是從*捕獲類*清單中選擇的。 捕獲類分為幾個類別,如下所述。

| 類別 | 描述 |
|--|--|
| 精確 | 這些捕獲類用於匹配特定事件類型,而沒有其他類型。 例如[,編譯器](cpp-event-data-types/compiler.md)類與[編譯器](event-table.md#compiler)事件匹配。 |
| 萬用字元 | 這些捕獲類可用於匹配其支援的事件清單中的任何事件。 例如,"[活動](cpp-event-data-types/activity.md)通配符"與任何活動事件匹配。 另一個範例是[編譯器Pass](cpp-event-data-types/compiler-pass.md)通配符,它可以匹配[FRONT_END_PASS](event-table.md#front-end-pass)或[BACK_END_PASS](event-table.md#back-end-pass)事件。 |
| 群組 | 組捕獲類的名稱以*組*結尾。 它們用於匹配一行中同一類型的多個事件,而忽略間隙。 它們僅在匹配遞歸事件時才有意義,因為您不知道事件堆疊中存在多少個。 例如,每次編譯器分析檔時,都會發生[FRONT_END_FILE](event-table.md#front-end-file)活動。 此活動是遞迴的,因為編譯器在分析檔時可能會找到包含指令。 [FrontEndFile](cpp-event-data-types/front-end-file.md)類僅匹配堆疊中一個FRONT_END_FILE事件。 使用[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)類匹配整個包含層次結構。 |
| 通配符群組 | 通配符組合並通配符和組的屬性。 此類別的唯一類是[調用組](cpp-event-data-types/invocation-group.md),它匹配和捕獲單個事件堆疊中的所有[LINKER](event-table.md#linker)和[編譯器](event-table.md#compiler)事件。 |

請參閱[事件表](event-table.md)以瞭解可以使用哪些捕獲類來匹配每個事件。

#### <a name="after-matching-using-captured-events"></a>符合後:使用捕捉的事件

符合成功完成後,`Match*`函數將建構捕獲類物件並將其轉發到指定的函數。 使用這些捕獲類對象訪問事件的屬性。

#### <a name="example"></a>範例

```cpp
AnalysisControl MyAnalyzer::OnStartActivity(const EventStack& eventStack)
{
    // The event types to match are specified in the PrintIncludes function
    // signature.  
    MatchEventStackInMemberFunction(eventStack, this, &MyAnalyzer::PrintIncludes);
}

// We want to capture event stacks where:
// 1. The current event is a FrontEndFile activity.
// 2. The current FrontEndFile activity has at least one parent FrontEndFile activity
//    and possibly many.
void PrintIncludes(FrontEndFileGroup parentIncludes, FrontEndFile currentFile)
{
    // Once we reach this point, the event stack we are interested in has been matched.
    // The current FrontEndFile activity has been captured into 'currentFile', and
    // its entire inclusion hierarchy has been captured in 'parentIncludes'.

    cout << "The current file being parsed is: " << currentFile.Path() << endl;
    cout << "This file was reached through the following inclusions:" << endl;

    for (auto& f : parentIncludes)
    {
        cout << f.Path() << endl;
    }
}
```

::: moniker-end

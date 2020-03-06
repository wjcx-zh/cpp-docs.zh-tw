---
title: C++Build Insights SDK
description: Visual Studio C++ BUILD Insights SDK 的總覽。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5aafcc65bc30de77131d1945c9f4e78361db14ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332394"
---
# <a name="c-build-insights-sdk"></a>C++Build Insights SDK

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

C++ BUILD insights SDK 是 api 的集合，可讓您在C++ Build Insights 平臺上建立個人化工具。 本頁提供高階總覽，協助您開始著手。

## <a name="obtaining-the-sdk"></a>取得 SDK

您可以遵循下列C++步驟，將 BUILD Insights SDK 下載為 NuGet 套件：

1. 從 Visual Studio 2017 和更新版本中，建立C++新的專案。
1. 在 [**方案總管**] 窗格中，以滑鼠右鍵按一下您的專案。
1. 從內容功能表中選取 [**管理 NuGet 套件**]。
1. 在右上方，選取 [ **nuget.org** ] 套件來源。
1. 搜尋 BuildInsights 套件的最新版本。
1. 選擇 [**安裝**]。
1. 接受授權。

如需 SDK 周圍一般概念的詳細資訊，請參閱。 您也可以存取官方[ C++ Build Insights 範例 GitHub 存放庫](https://github.com/microsoft/cpp-build-insights-samples)，以查看使用 SDK C++的實際應用程式範例。

## <a name="collecting-a-trace"></a>收集追蹤

使用C++ BUILD Insights SDK 來分析來自 MSVC 工具鏈的事件，需要您先收集追蹤。 SDK 會使用 Windows 事件追蹤（ETW）作為基礎追蹤技術。 您可以透過兩種方式來收集追蹤：

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法1：在 Visual Studio 2019 和更新版本中使用 vcperf

1. 為 VS 2019 開啟提高許可權的 x64 Native Tools 命令提示字元。
1. 執行下列命令： `vcperf /start MySessionName`
1. 建置您的專案。
1. 執行下列命令： `vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > 在使用 vcperf 停止追蹤時，請使用 `/stopnoanalyze` 命令。 您無法使用C++ BUILD Insights SDK 來分析正則 `/stop` 命令所停止的追蹤。

### <a name="method-2-programmatically"></a>方法2：以程式設計方式

使用任何這些C++ BUILD Insights SDK 追蹤集合函數，以程式設計方式啟動和停止追蹤。 **執行這些函式呼叫的程式必須具有系統管理許可權。** 只有啟動和停止追蹤功能需要系統管理許可權。 Build Insights SDK 中的C++所有其他函式都可以在沒有這些函式的情況下執行。

### <a name="sdk-functions-related-to-trace-collection"></a>與追蹤集合相關的 SDK 函數

| 功能 | C++ API | C API |
|--|--|--|
| 啟動追蹤 | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| 停止追蹤 | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| 停止追蹤和<br />立即分析結果 | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| 停止追蹤和<br />立即 relogging 結果 | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

下列各節會示範如何設定分析或 relogging 會話。 這是合併功能函式的必要參數，例如[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md)。

## <a name="consuming-a-trace"></a>使用追蹤

有了 ETW 追蹤之後，請使用C++ BUILD Insights SDK 將它解壓縮。 SDK 會提供您一個格式的事件，讓您能夠快速開發工具。 我們不建議您在不使用 SDK 的情況下，使用原始的 ETW 追蹤。 MSVC 所使用的事件格式尚未記載，已優化而無法調整為大型組建，且難以理解。 此外， C++ BUILD INSIGHTS SDK API 會穩定，而原始 ETW 追蹤格式可能會變更，恕不另行通知。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>與追蹤耗用量相關的 SDK 類型和函數

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 設定事件回呼 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C++ BUILD Insights SDK 會透過回呼函式提供事件。 在C++中，藉由建立會繼承 IAnalyzer 或 IRelogger 介面的分析器或 relogger 類別，來執行回呼函式。 在 C 中，實作用於全域函式中的回呼，並在 ANALYSIS_CALLBACKS 或 RELOG_CALLBACKS 結構中提供指標給它們。 |
| 建立群組 | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | C++ API 提供 helper 函式和類型，以將多個分析器和 relogger 物件群組在一起。 群組是將複雜分析分成更簡單步驟的一種方式。 [vcperf](https://github.com/microsoft/vcperf)是以這種方式組織。 |
| 分析或 relogging | [分析](functions/analyze.md)<br />[重新記錄](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>分析和 relogging

使用追蹤是透過分析會話或 relogging 會話來完成。

使用一般分析適用于大部分的案例。 這個方法可讓您彈性地選擇您的輸出格式： `printf` 文字、xml、JSON、資料庫、REST 呼叫等等。

Relogging 適用于需要產生 ETW 輸出檔的特殊用途分析。 使用 relogging，您可以將組建C++深入解析事件轉譯成您自己的 ETW 事件格式。 適當的 relogging 使用方式是將C++組建深入解析資料與現有的 ETW 工具和基礎結構連結在一起。 例如， [vcperf](https://github.com/microsoft/vcperf)會使用 relogging 介面。 這是因為它必須產生 Windows Performance Analyzer （ETW 工具）可以瞭解的資料。 如果您打算使用 relogging 介面，就必須先瞭解 ETW 的運作方式。

### <a name="creating-analyzer-groups"></a>建立分析器群組

請務必瞭解如何建立群組。 以下範例顯示如何建立會列印*Hello，world！* 的分析器群組！ 它收到的每個活動啟動事件。

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

### <a name="sdk-types-and-functions-related-to-events"></a>與事件相關的 SDK 類型和函式

| 功能 | C++ API | C API | 注意 |
|--|--|--|--|
| 比對和篩選事件 | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | 此C++ API 提供的函式可讓您輕鬆地從追蹤中將您關心的事件解壓縮。 使用 C API 時，必須手動完成此篩選。 |
| 事件資料類型 | [活動](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[Nswag.codegeneration.csharp](cpp-event-data-types/code-generation.md)<br />[命令列](cpp-event-data-types/command-line.md)<br />[編譯器](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[事件](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[引動過程](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[LibOutput](cpp-event-data-types/lib-output.md)<br />[連結器](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1.log](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[Thread](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>活動和簡單事件

事件分為兩類：*活動*和*簡單事件*。 活動是正在進行的進程，其具有開始和結束的時間。 簡單事件是精確出現的，而且沒有持續時間。 使用C++ BUILD Insights SDK 來分析 MSVC 追蹤時，您會在活動啟動和停止時收到個別事件。 只有在發生簡單事件時，您才會收到一個事件。

### <a name="parent-child-relationships"></a>父子式關聯性

活動和簡單事件會透過父子式關聯性彼此相關。 活動或簡單事件的父系是其發生所在的活動。 例如，編譯原始程式檔時，編譯器必須剖析檔案，然後產生程式碼。 剖析和程式碼產生活動都是編譯器活動的子系。

簡單事件不會有持續時間，因此不會發生任何其他情況。 如此一來，他們就不會有任何子系。

[事件資料表](event-table.md)中會指出每個活動和簡單事件的父子式關聯性。 使用C++ Build Insights 事件時，瞭解這些關聯性是很重要的。 您通常必須依賴它們來瞭解事件的完整內容。

### <a name="properties"></a>屬性

所有事件都具有下列屬性：

| 屬性 | 描述 |
|--|--|
| 類型識別碼 | 可唯一識別事件種類的數位。 |
| 實例識別碼 | 可唯一識別追蹤內事件的數位。 如果追蹤中出現兩個相同類型的事件，則兩者都會取得唯一的實例識別碼。 |
| 開始時間 | 活動開始的時間，或發生簡單事件的時間。 |
| 處理序識別碼 | 識別發生事件之進程的數位。 |
| 執行緒識別碼 | 識別發生事件之執行緒的數位。 |
| 處理器索引 | 以零為基底的索引，表示事件發出的邏輯處理器。 |
| 事件名稱 | 描述事件種類的字串。 |

簡單事件以外的所有活動也具有下列屬性：

| 屬性 | 描述 |
|--|--|
| 停止時間 | 活動停止的時間。 |
| 專有持續時間 | 在活動中花費的時間，不包括在其子活動中花費的時間。 |
| CPU 時間 | CPU 花費在附加至活動的執行緒中執行程式碼的時間。 它不包含附加至活動的執行緒進入睡眠狀態的時間。 |
| 專屬 CPU 時間 | 與 CPU 時間相同，但不包括子活動所花費的 CPU 時間。 |
| 時鐘時間責任 | 活動對整體時鐘時間的貢獻。 時鐘時間責任會考慮活動之間的平行處理。 例如，假設兩個不相關的活動平行執行。 兩者的持續時間為10秒，且完全相同的開始和停止時間。 在此情況下，組建深入解析會指派5秒的時鐘時間責任。 相反地，如果這些活動是在另一個以外的地方執行，而不重迭，它們就會被指派10秒的時鐘時間責任。 |
| 專屬的時鐘時間責任 | 與時鐘時間責任相同，但不包括子活動的時鐘時間責任。 |

有些事件的屬性超出所述的內容。 在此情況下，這些額外的屬性會列在[事件資料表](event-table.md)中。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>使用 Build Insights SDK 所C++提供的事件

#### <a name="the-event-stack"></a>事件堆疊

每當C++ BUILD Insights SDK 提供您事件時，它就會以堆疊的形式呈現。 堆疊中的最後一個專案是目前的事件，而專案則是其父階層。 例如， [LTCG](event-table.md#ltcg)啟動和停止事件會在連結器的 pass 1 期間發生。 在此情況下，您收到的堆疊包含： \[[連結器](event-table.md#linker)、 [pass1.log](event-table.md#pass1)、LTCG\]。 父階層很方便，因為您可以將事件追蹤至其根。 如果上述 LTCG 活動的速度很慢，您可以立即瞭解所牽涉的連結器調用。

#### <a name="matching-events-and-event-stacks"></a>比對事件和事件堆疊

C++ BUILD Insights SDK 會為您提供追蹤中的每個事件，但大部分的時候，您都只在意其中的一部分。 在某些情況下，您可能只在意*事件堆疊*的子集。 SDK 提供的設備可協助您快速解壓縮所需的事件或事件堆疊，並拒絕您不需要的專案。 這會透過這些比對功能來完成：

|  |  |
|--|--|
| [MatchEvent](functions/match-event.md) | 如果符合其中一個指定的類型，請保留一個事件。 將相符的事件轉送至 lambda 或其他可呼叫的類型。 此函式不會考慮事件的父階層。 |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | 如果符合成員函式的參數中所指定的類型，請保留事件。 將相符的事件轉送至成員函式。 此函式不會考慮事件的父階層。 |
| [MatchEventStack](functions/match-event-stack.md) | 如果事件和其父階層都符合指定的類型，請保留事件。 將事件和相符的父階層事件轉送至 lambda 或其他可呼叫的類型。 |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | 如果事件和其父階層都符合成員函式的參數清單中指定的類型，請保留事件。 將事件和相符的父階層事件轉送至成員函式。 |

當描述要比對的父階層時，事件堆疊比對函式（例如 `MatchEventStack` 允許間距）。 例如，您可以說您對 \[[連結器](event-table.md#linker) [LTCG](event-table.md#ltcg)\] 堆疊感興趣。 它也會符合 \[連結器、 [pass1.log](event-table.md#pass1)、LTCG\] 堆疊。 指定的最後一個類型必須是要符合的事件種類，而且不是父階層的一部分。

#### <a name="capture-classes"></a>Capture 類別

您必須指定要比對的類型，才能使用 `Match*` 函數。 這些類型是從*capture 類別*清單中選取的。 Capture 類別有幾個分類，如下所述。

| 類別 | 描述 |
|--|--|
| 精確 | 這些 capture 類別是用來比對特定的事件種類，而不是任何其他。 其中一個範例是符合[編譯器](event-table.md#compiler)事件的[編譯器](cpp-event-data-types/compiler.md)類別。 |
| 萬用字元 | 這些 capture 類別可以用來比對所支援事件清單中的任何事件。 例如，[活動](cpp-event-data-types/activity.md)萬用字元會符合任何活動事件。 另一個範例是[CompilerPass](cpp-event-data-types/compiler-pass.md)萬用字元，它可以符合[FRONT_END_PASS](event-table.md#front-end-pass)或[BACK_END_PASS](event-table.md#back-end-pass)事件。 |
| 群組 | 群組捕捉類別的名稱以*群組*結尾。 它們會用來比對資料列中相同類型的多個事件，並忽略間距。 它們只有在符合遞迴事件時才有意義，因為您不知道事件堆疊中有多少存在。 例如，每次編譯器剖析檔案時，就會發生[FRONT_END_FILE](event-table.md#front-end-file)活動。 這個活動是遞迴的，因為編譯器在剖析檔案時，可能會發現 include 指示詞。 [FrontEndFile](cpp-event-data-types/front-end-file.md)類別只符合堆疊中的一個 FRONT_END_FILE 事件。 使用[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)類別，以符合整個 include 階層。 |
| 萬用字元群組 | 萬用字元群組會合並萬用字元和群組的屬性。 這個類別的唯一類別是[InvocationGroup](cpp-event-data-types/invocation-group.md)，它符合並捕捉單一事件堆疊中的所有[連結器](event-table.md#linker)和[編譯器](event-table.md#compiler)事件。 |

請參閱[事件資料表](event-table.md)，瞭解哪些 capture 類別可以用來比對每個事件。

#### <a name="after-matching-using-captured-events"></a>比對之後：使用已捕捉的事件

一旦比對成功完成，`Match*` 函式會建立 capture 類別物件，並將其轉送至指定的函式。 使用這些 capture 類別物件來存取事件的屬性。

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

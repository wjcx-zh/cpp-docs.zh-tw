---
title: C++ 組建見解 SDK
description: Visual Studio c + + Build Insights SDK 的總覽。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyzing
- Relogging
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f53a9b6c682a0af7d8a01f6378ed0574d8fa4ca
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041168"
---
# <a name="c-build-insights-sdk"></a>C++ 組建見解 SDK

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

C + + Build Insights SDK 是 Api 的集合，可讓您在 c + + Build Insights 平臺之上建立個人化工具。 本頁面提供概要說明，協助您開始使用。

## <a name="obtaining-the-sdk"></a>取得 SDK

您可以遵循下列步驟，以 NuGet 套件的形式下載 c + + Build Insights SDK：

1. 在 Visual Studio 2017 和更新版本中，建立新的 c + + 專案。
1. 在 [ **方案總管** ] 窗格中，以滑鼠右鍵按一下您的專案。
1. 從內容功能表中選取 [ **管理 NuGet 套件** ]。
1. 選取右上方的 [ **nuget.org** 套件來源]。
1. 搜尋最新版本的 BuildInsights 套件。
1. 選擇 [ **安裝**]。
1. 接受授權。

如需 SDK 周圍的一般概念的詳細資訊，請參閱。 您也可以存取官方的 [c + + Build Insights 範例 GitHub 存放庫](https://github.com/microsoft/cpp-build-insights-samples) ，以查看使用 SDK 的實際 c + + 應用程式範例。

## <a name="collecting-a-trace"></a>收集追蹤

使用 c + + Build Insights SDK 來分析 MSVC 工具鏈所推出的事件時，需要先收集追蹤。 SDK 利用 Windows (ETW) 的事件追蹤作為基礎追蹤技術。 您可以透過兩種方式來收集追蹤：

### <a name="method-1-using-vcperf-in-visual-studio-2019-and-above"></a>方法1：在 Visual Studio 2019 和更新版本中使用 vcperf

1. 開啟 VS 2019 的提高許可權 x64 Native Tools 命令提示字元。
1. 執行下列命令：`vcperf /start MySessionName`
1. 建置您的專案。
1. 執行下列命令：`vcperf /stopnoanalyze MySessionName outputTraceFile.etl`

   > [!IMPORTANT]
   > 使用 `/stopnoanalyze` vcperf 停止您的追蹤時，請使用命令。 您無法使用 c + + Build Insights SDK 來分析由一般命令停止的追蹤 `/stop` 。

### <a name="method-2-programmatically"></a>方法2：以程式設計方式

使用任何這些 c + + Build Insights SDK 追蹤集合函數，以程式設計方式啟動和停止追蹤。 **執行這些函式呼叫的程式必須具有系統管理許可權。** 只有啟動和停止追蹤函數需要系統管理許可權。 C + + Build Insights SDK 中的所有其他函式都可以在沒有它們的情況下執行。

### <a name="sdk-functions-related-to-trace-collection"></a>與追蹤集合相關的 SDK 函數

| 功能 | C++ API | C API |
|--|--|--|
| 啟動追蹤 | [StartTracingSession](functions/start-tracing-session.md) | [StartTracingSessionA](functions/start-tracing-session-a.md)<br />[StartTracingSessionW](functions/start-tracing-session-w.md) |
| 停止追蹤 | [StopTracingSession](functions/stop-tracing-session.md) | [StopTracingSessionA](functions/stop-tracing-session-a.md)<br />[StopTracingSessionW](functions/stop-tracing-session-w.md) |
| 停止追蹤和<br />立即分析結果 | [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md) | [StopAndAnalyzeTracingSessionA](functions/stop-and-analyze-tracing-session-a.md)<br />[StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session-w.md) |
| 停止追蹤和<br />立即 relogging 結果 | [StopAndRelogTracingSession](functions/stop-and-relog-tracing-session.md) | [StopAndRelogTracingSessionA](functions/stop-and-relog-tracing-session-a.md)<br />[StopAndRelogTracingSessionW](functions/stop-and-relog-tracing-session-w.md) |

接下來的各節會示範如何設定分析或 relogging 會話。 這是合併功能函式的必要功能，例如 [StopAndAnalyzeTracingSession](functions/stop-and-analyze-tracing-session.md)。

## <a name="consuming-a-trace"></a>使用追蹤

當您有 ETW 追蹤之後，請使用 c + + Build Insights SDK 將它解壓縮。 SDK 提供您可讓您快速開發工具的格式事件。 我們不建議您在不使用 SDK 的情況下使用未經處理的 ETW 追蹤。 MSVC 所使用的事件格式未記載，已優化以調整為大型組建，而且難以理解。 此外，c + + Build Insights SDK API 是穩定的，而原始 ETW 追蹤格式可能會變更，恕不另行通知。

### <a name="sdk-types-and-functions-related-to-trace-consumption"></a>與追蹤耗用量相關的 SDK 類型和函式

| 功能 | C++ API | C API | 備註 |
|--|--|--|--|
| 設定事件回呼 | [IAnalyzer](other-types/ianalyzer-class.md)<br />[IRelogger](other-types/irelogger-class.md) | [ANALYSIS_CALLBACKS](other-types/analysis-callbacks-struct.md)<br />[RELOG_CALLBACKS](other-types/relog-callbacks-struct.md) | C + + Build Insights SDK 透過回呼函數提供事件。 在 c + + 中，藉由建立可繼承 IAnalyzer 或 IRelogger 介面的分析器或 relogger 類別來執行回呼函數。 在 C 中，執行全域函式中的回呼，並在 ANALYSIS_CALLBACKS 或 RELOG_CALLBACKS 結構中提供它們的指標。 |
| 建立群組 | [MakeStaticAnalyzerGroup](functions/make-static-analyzer-group.md)<br />[MakeStaticReloggerGroup](functions/make-static-relogger-group.md)<br />[MakeDynamicAnalyzerGroup](functions/make-dynamic-analyzer-group.md)<br />[MakeDynamicReloggerGroup](functions/make-dynamic-relogger-group.md) |  | C + + API 提供 helper 函式和型別，以將多個分析器和 relogger 物件群組在一起。 群組是將複雜的分析分成更簡單步驟的好方法。 [vcperf](https://github.com/microsoft/vcperf) 是以這種方式組織。 |
| 分析或 relogging | [分析](functions/analyze.md)<br />[重新記錄](functions/relog.md) | [AnalyzeA](functions/analyze-a.md)<br />[AnalyzeW](functions/analyze-w.md)<br />[RelogA](functions/relog-a.md)<br />[RelogW](functions/relog-w.md) |  |

### <a name="analyzing-and-relogging"></a>分析和 relogging

使用追蹤是透過分析會話或 relogging 會話來完成。

使用一般分析適用于大部分的案例。 此方法可讓您彈性地選擇輸出格式： `printf` text、xml、JSON、database、REST 呼叫等等。

Relogging 適用于需要產生 ETW 輸出檔的特殊用途分析。 使用 relogging，您可以將 c + + Build Insights 事件轉譯成您自己的 ETW 事件格式。 Relogging 的適當用途是將 c + + Build Insights 資料連結至您現有的 ETW 工具和基礎結構。 例如， [vcperf](https://github.com/microsoft/vcperf) 會使用 relogging 介面。 這是因為它必須產生 Windows Performance Analyzer 的資料，也就是 ETW 工具可以瞭解的。 如果您打算使用 relogging 介面，則必須事先瞭解 ETW 的運作方式。

### <a name="creating-analyzer-groups"></a>建立分析器群組

請務必瞭解如何建立群組。 以下範例顯示如何建立可列印*Hello，world！* 的分析器群組 針對它收到的每個活動開始事件。

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

| 功能 | C++ API | C API | 備註 |
|--|--|--|--|
| 比對和篩選事件 | [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md)<br />[MatchEventStack](functions/match-event-stack.md)<br />[MatchEventInMemberFunction](functions/match-event-in-member-function.md)<br />[MatchEvent](functions/match-event.md) |  | C + + API 提供的函式可讓您輕鬆地從追蹤中解壓縮您在意的事件。 使用 C API 時，必須手動完成這項篩選。 |
| 事件資料類型 | [活動](cpp-event-data-types/activity.md)<br />[BackEndPass](cpp-event-data-types/back-end-pass.md)<br />[BottomUp](cpp-event-data-types/bottom-up.md)<br />[C1DLL](cpp-event-data-types/c1-dll.md)<br />[C2DLL](cpp-event-data-types/c2-dll.md)<br />[CodeGeneration](cpp-event-data-types/code-generation.md)<br />[CommandLine](cpp-event-data-types/command-line.md)<br />[編譯 器](cpp-event-data-types/compiler.md)<br />[CompilerPass](cpp-event-data-types/compiler-pass.md)<br />[EnvironmentVariable](cpp-event-data-types/environment-variable.md)<br />[事件](cpp-event-data-types/event.md)<br />[EventGroup](cpp-event-data-types/event-group.md)<br />[EventStack](cpp-event-data-types/event-stack.md)<br />[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md)<br />[ExpOutput](cpp-event-data-types/exp-output.md)<br />[FileInput](cpp-event-data-types/file-input.md)<br />[FileOutput](cpp-event-data-types/file-output.md)<br />[ForceInlinee](cpp-event-data-types/force-inlinee.md)<br />[FrontEndFile](cpp-event-data-types/front-end-file.md)<br />[FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md)<br />[FrontEndPass](cpp-event-data-types/front-end-pass.md)<br />[Function](cpp-event-data-types/function.md)<br />[ImpLibOutput](cpp-event-data-types/imp-lib-output.md)<br />[引動過程](cpp-event-data-types/invocation.md)<br />[InvocationGroup](cpp-event-data-types/invocation-group.md)<br />[ImpLibOutput](cpp-event-data-types/lib-output.md)<br />[連結器](cpp-event-data-types/linker.md)<br />[LinkerGroup](cpp-event-data-types/linker-group.md)<br />[LinkerPass](cpp-event-data-types/linker-pass.md)<br />[LTCG](cpp-event-data-types/ltcg.md)<br />[ObjOutput](cpp-event-data-types/obj-output.md)<br />[OptICF](cpp-event-data-types/opt-icf.md)<br />[OptLBR](cpp-event-data-types/opt-lbr.md)<br />[OptRef](cpp-event-data-types/opt-ref.md)<br />[Pass1](cpp-event-data-types/pass1.md)<br />[Pass2](cpp-event-data-types/pass2.md)<br />[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md)<br />[SimpleEvent](cpp-event-data-types/simple-event.md)<br />[SymbolName](cpp-event-data-types/symbol-name.md)<br />[TemplateInstantiation](cpp-event-data-types/template-instantiation.md)<br />[TemplateInstantiationGroup](cpp-event-data-types/template-instantiation-group.md)<br />[執行緒](cpp-event-data-types/thread.md)<br />[TopDown](cpp-event-data-types/top-down.md)<br />[TraceInfo](cpp-event-data-types/trace-info.md)<br />[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) | [CL_PASS_DATA](c-event-data-types/cl-pass-data-struct.md)<br />[EVENT_COLLECTION_DATA](c-event-data-types/event-collection-data-struct.md)<br />[EVENT_DATA](c-event-data-types/event-data-struct.md)<br />[EVENT_ID](c-event-data-types/event-id-enum.md)<br />[FILE_DATA](c-event-data-types/file-data-struct.md)<br />[FILE_TYPE_CODE](c-event-data-types/file-type-code-enum.md)<br />[FRONT_END_FILE_DATA](c-event-data-types/front-end-file-data-struct.md)<br />[FUNCTION_DATA](c-event-data-types/function-data-struct.md)<br />[FUNCTION_FORCE_INLINEE_DATA](c-event-data-types/function-force-inlinee-data-struct.md)<br />[INVOCATION_DATA](c-event-data-types/invocation-data-struct.md)<br />[INVOCATION_VERSION_DATA](c-event-data-types/invocation-version-data-struct.md)<br />[MSVC_TOOL_CODE](c-event-data-types/msvc-tool-code-enum.md)<br />[NAME_VALUE_PAIR_DATA](c-event-data-types/name-value-pair-data-struct.md)<br />[SYMBOL_NAME_DATA](c-event-data-types/symbol-name-data-struct.md)<br />[TEMPLATE_INSTANTIATION_DATA](c-event-data-types/template-instantiation-data-struct.md)<br />[TEMPLATE_INSTANTIATION_KIND_CODE](c-event-data-types/template-instantiation-kind-code-enum.md)<br />[TRACE_INFO_DATA](c-event-data-types/trace-info-data-struct.md)<br />[TRANSLATION_UNIT_PASS_CODE](c-event-data-types/translation-unit-pass-code-enum.md) |  |

### <a name="activities-and-simple-events"></a>活動和簡單事件

事件分為兩種類別： *活動* 和 *簡單事件*。 活動是以開始和結束的時間進行中的進程。 簡單事件是精確出現，沒有持續時間。 使用 c + + Build Insights SDK 分析 MSVC 追蹤時，當活動開始和停止時，您將會收到個別的事件。 當簡單事件發生時，您只會收到一個事件。

### <a name="parent-child-relationships"></a>父子式關聯性

活動和簡單事件透過父子式關聯性彼此相關。 活動或簡單事件的父系是它們發生所在的內含活動。 例如，編譯原始程式檔時，編譯器必須剖析檔案，然後產生程式碼。 剖析和程式碼產生活動都是編譯器活動的子系。

簡單事件不會有持續時間，因此不會發生任何其他事件。 因此，他們永遠都沒有任何子系。

每個活動和簡單事件的父子式關聯性會在 [事件資料表](event-table.md)中指出。 使用 c + + Build Insights 事件時，瞭解這些關聯性是很重要的。 您通常必須依賴它們來瞭解事件的完整內容。

### <a name="properties"></a>屬性

所有事件都有下列屬性：

| 屬性 | 描述 |
|--|--|
| 類型識別碼 | 可唯一識別事件種類的數位。 |
| 實例識別碼 | 可唯一識別追蹤內事件的數位。 如果追蹤中發生相同類型的兩個事件，則會取得唯一的實例識別碼。 |
| 開始時間 | 活動開始的時間，或發生簡單事件的時間。 |
| 處理序識別碼 | 識別發生事件之進程的數位。 |
| 執行緒識別碼 | 識別發生事件之執行緒的數位。 |
| 處理器索引 | 以零為基底的索引，表示事件發出的邏輯處理器。 |
| 事件名稱 | 描述事件種類的字串。 |

簡單事件以外的所有活動也都有下列屬性：

| 屬性 | 描述 |
|--|--|
| 停止時間 | 活動停止的時間。 |
| 專屬持續時間 | 活動花費的時間，不包括其子活動所花費的時間。 |
| CPU 時間 | CPU 花費在附加至活動的執行緒中執行程式碼的時間。 它不包含附加至活動之執行緒的睡眠時間。 |
| 專屬 CPU 時間 | 與 CPU 時間相同，但不包括子活動所花費的 CPU 時間。 |
| 時鐘時間責任 | 活動對整體時鐘時間的貢獻。 時鐘時間的責任會考慮活動之間的平行處理原則。 例如，假設兩個不相關的活動會以平行方式執行。 兩者都有10秒的持續時間，以及完全相同的開始和停止時間。 在此情況下，Build Insights 會將時鐘時間的責任指派為5秒。 相反地，如果這些活動是在另一個沒有重迭的情況下執行，它們都會被指派時間為10秒的時鐘時間責任。 |
| 專屬的時鐘時間責任 | 如同時鐘時間的責任，但會排除子活動的時鐘時間責任。 |

有些事件除了所述的內容之外，還有自己的屬性。 在此情況下，這些額外的屬性會列在 [事件資料表](event-table.md)中。

### <a name="consuming-events-provided-by-the-c-build-insights-sdk"></a>使用 c + + Build Insights SDK 提供的事件

#### <a name="the-event-stack"></a>事件堆疊

每當 c + + Build Insights SDK 提供您事件時，它就會以堆疊的形式呈現。 堆疊中的最後一個專案是目前的事件，以及其父階層之前的專案。 例如， [LTCG](event-table.md#ltcg) 啟動和停止事件會在連結器的傳遞1期間發生。 在此情況下，您收到的堆疊包含： \[ [連結器](event-table.md#linker)、 [pass1.log](event-table.md#pass1)、LTCG \] 。 父階層很方便，因為您可以將事件追溯到其根。 如果上述 LTCG 活動的速度很慢，您可以立即瞭解牽涉到的連結器調用。

#### <a name="matching-events-and-event-stacks"></a>相符的事件和事件堆疊

C + + Build Insights SDK 可為您提供追蹤中的每個事件，但大部分的情況下，您只在意一部分的事件。 在某些情況下，您可能只在意 *事件堆疊*的子集。 SDK 提供的工具可協助您快速將所需的事件或事件堆疊解壓縮，並拒絕您不需要的事件。 這是透過這些相符的函式來完成的：

| 函式 | 描述 |
|--|--|
| [MatchEvent](functions/match-event.md) | 如果它符合其中一個指定的類型，請保留事件。 將相符的事件轉送至 lambda 或其他可呼叫的類型。 此函數不會考慮事件的父階層。 |
| [MatchEventInMemberFunction](functions/match-event-in-member-function.md) | 如果事件符合成員函式參數中所指定的類型，則保留事件。 將相符的事件轉送到成員函式。 此函數不會考慮事件的父階層。 |
| [MatchEventStack](functions/match-event-stack.md) | 如果事件和其父階層符合指定的類型，則保留事件。 將事件和相符的父階層事件轉寄至 lambda 或其他可呼叫的類型。 |
| [MatchEventStackInMemberFunction](functions/match-event-stack-in-member-function.md) | 如果事件和其父階層符合成員函式參數清單中指定的類型，則保留事件。 將事件和相符的父階層事件轉送到成員函式。 |

在描述要比對的父階層時，事件堆疊比對函式，例如 `MatchEventStack` 允許間距。 例如，您可以說是您對 \[ [連結器](event-table.md#linker) [LTCG](event-table.md#ltcg) \] 堆疊感興趣。 它也會符合 \[ 連結器、 [Pass1.log](event-table.md#pass1)、LTCG \] 堆疊。 最後指定的型別必須是要比對的事件種類，而且不是父階層的一部分。

#### <a name="capture-classes"></a>Capture 類別

使用函式 `Match*` 時，您必須指定要比對的類型。 這些類型是從 *capture 類別*清單中選取的。 Capture 類別有幾個類別，如下所述。

| 類別 | 描述 |
|--|--|
| 精確 | 這些 capture 類別是用來比對特定事件種類，而不是其他事件種類。 其中一個範例是與[編譯器](event-table.md#compiler)事件相符的[編譯器](cpp-event-data-types/compiler.md)類別。 |
| 萬用字元 | 這些 capture 類別可以用來比對它們所支援之事件清單中的任何事件。 例如， [活動](cpp-event-data-types/activity.md) 萬用字元會符合任何活動事件。 另一個範例是 [CompilerPass](cpp-event-data-types/compiler-pass.md) 萬用字元，它可以符合 [FRONT_END_PASS](event-table.md#front-end-pass) 或 [BACK_END_PASS](event-table.md#back-end-pass) 事件。 |
| Group | 群組捕獲類別的名稱以 *群組*結尾。 它們是用來比對資料列中相同類型的多個事件，並忽略間距。 它們只有在符合遞迴事件時才有意義，因為您不知道事件堆疊中有多少存在。 例如，每次編譯器剖析檔案時，就會發生 [FRONT_END_FILE](event-table.md#front-end-file) 活動。 此活動是遞迴的，因為編譯器在剖析檔案時，可能會發現 include 指示詞。 [FrontEndFile](cpp-event-data-types/front-end-file.md)類別僅符合堆疊中的一個 FRONT_END_FILE 事件。 使用 [FrontEndFileGroup](cpp-event-data-types/front-end-file-group.md) 類別來比對整個 include 階層。 |
| 萬用字元群組 | 萬用字元群組結合萬用字元和群組的屬性。 這個類別目錄的唯一類別是 [InvocationGroup](cpp-event-data-types/invocation-group.md)，它會比對和捕捉單一事件堆疊中的所有 [連結器](event-table.md#linker) 和 [編譯器](event-table.md#compiler) 事件。 |

請參閱 [事件表格](event-table.md) ，以瞭解可以使用哪些 capture 類別來比對每個事件。

#### <a name="after-matching-using-captured-events"></a>符合之後：使用已捕捉的事件

一旦相符專案順利完成，函式 `Match*` 就會建立 capture 類別物件，並將它們轉送到指定的函式。 使用這些 capture 類別物件來存取事件的屬性。

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

---
title: C + + Build Insights SDK：事件資料表
description: Visual Studio c + + Build Insights SDK 的事件參考
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b1cf6871329fcce3166495e173360a88ac38ee0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224210"
---
# <a name="c-build-insights-sdk-event-table"></a>C + + Build Insights SDK：事件資料表

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>編譯程式事件

[編譯器](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>編譯器前端事件

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>編譯器後端事件

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[執行緒](#thread)\
[函數](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>連結器事件

[連結器](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1.LOG](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>事件資料表

| 事件 | 屬性 | 說明 |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | 類型 | 活動 |
|  | Parents | [編譯器](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | 屬性 | -輸入來源檔案的絕對路徑<br/>-輸出物件檔案的絕對路徑 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | 說明 | 在編譯器後端階段啟動和停止時發生。 此階段會負責優化剖析的 C/c + + 原始程式碼，並將它轉換成機器碼。 |
| <a name="bottom-up"></a>BOTTOM_UP | 類型 | 活動 |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | 說明 | 在整個程式分析的開始和停止「下一階段」時發生。 |
| <a name="c1-dll"></a>C1_DLL | 類型 | 活動 |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | 說明 | 在*c1.dll*或*c1xx.dll*調用的開始和停止時發生。 這些 Dll 是編譯器的 C 和 c + + 前端。 它們只會由編譯器驅動程式（*cl.exe*）來叫用。 |
| <a name="c2-dll"></a>C2_DLL | 類型 | 活動 |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | 說明 | 在*c2.dll*調用的開始和停止時發生。 這個 DLL 是編譯器的後端。 編譯器驅動程式（*cl.exe*）會呼叫它。 當使用連結時間程式碼產生時，連結器（*link.exe*）也會叫用它。 |
| <a name="code-generation"></a>CODE_GENERATION | 類型 | 活動 |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [函數](#function)<br/>[執行緒](#thread) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | 說明 | 在後端的程式碼產生階段開始和停止時發生。 |
| <a name="command-line"></a>COMMAND_LINE | 類型 | 簡單事件 |
|  | Parents | [編譯器](#compiler)<br/>[連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -用來叫用*cl.exe*或*link.exe*的命令列 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | 說明 | 編譯器和連結器完成評估命令列時發生。 評估的命令列會包含所有透過回應檔傳遞的*cl.exe*和*link.exe*參數。 它也包含*cl.exe*的參數，以及透過 cl、 *link.exe* \_ cl \_ 、link 和 link 等環境變數所傳遞的link.exe\_ \_ 。 |
| <a name="compiler"></a>編譯器 | 類型 | 活動 |
|  | Parents | 無 |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | 屬性 | -編譯器版本<br/>-工作目錄<br/>-所叫用之*cl.exe*的絕對路徑 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[引動過程](cpp-event-data-types/invocation.md)<br/>[編譯器](cpp-event-data-types/compiler.md) |
|  | 說明 | 在*cl.exe*調用的開始和停止時發生。 |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | 類型 | 簡單事件 |
|  | Parents | [編譯器](#compiler)<br/>[連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -環境變數的名稱<br/>-環境變數的值。 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | 說明 | 當叫用*cl.exe*或*link.exe*時，每個現有環境變數都會發生一次。 |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -DLL 或可執行檔輸出檔的絕對路徑。 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | 說明 | 其中一個連結器輸入為 DLL 或可執行檔映射檔案時發生。 |
| <a name="exp-output"></a>EXP_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | - *.Exp*輸出檔的絕對路徑。 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | 說明 | 其中一個連結器輸出為 *.exp*檔案時發生。 |
| <a name="file-input"></a>FILE_INPUT | 類型 | 簡單事件 |
|  | Parents | [編譯器](#compiler)<br/>[連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -輸入檔的絕對路徑<br/>-輸入檔的類型 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | 說明 | 發生于宣告*cl.exe*或*link.exe*輸入。 |
| <a name="force-inlinee"></a>FORCE_INLINEE | 類型 | 簡單事件 |
|  | Parents | [函數](#function) |
|  | Children | 無 |
|  | 屬性 | -強制內嵌函式的名稱。<br/>-強制內嵌函數的大小，以中繼指令計數表示。 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | 說明 | 當函式透過使用關鍵字而強制內嵌至另一個函數時發生 **`__forceinline`** 。 |
| <a name="front-end-file"></a>FRONT_END_FILE | 類型 | 活動 |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | -檔案的絕對路徑。 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | 說明 | 當編譯器前端啟動和停止處理檔案時發生。 這個事件是遞迴的。 當前端正在剖析包含的檔案時，就會發生遞迴。 |
| <a name="front-end-pass"></a>FRONT_END_PASS | 類型 | 活動 |
|  | Parents | [編譯器](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | 屬性 | -輸入來源檔案的絕對路徑<br/>-輸出物件檔案的絕對路徑 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | 說明 | 在編譯器前端階段啟動和停止時發生。 這個階段會負責剖析 C/c + + 原始程式碼，並將它轉換成中繼語言。 |
| <a name="function"></a>函數 | 類型 | 活動 |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[執行緒](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | 屬性 | -函數的名稱 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | 說明 | 開始和結束產生函式的程式碼時發生。 |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -匯入程式庫輸出檔案的絕對路徑。 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | 說明 | 當其中一個連結器的輸出是匯入程式庫時發生。 |
| <a name="lib-output"></a>LIB_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | -靜態程式庫輸出檔案的絕對路徑。 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/lib-output.md) |
|  | 說明 | 其中一個連結器的輸出為靜態程式庫時發生。 |
| <a name="linker"></a>連結器 | 類型 | 活動 |
|  | Parents | 無 |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1.LOG](#pass1)<br/>[PASS2](#pass2) |
|  | 屬性 | -連結器版本<br/>-工作目錄<br/>-所叫用之*link.exe*的絕對路徑 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[引動過程](cpp-event-data-types/invocation.md)<br/>[連結器](cpp-event-data-types/linker.md) |
|  | 說明 | 在*link.exe*調用的開始和停止時發生。 |
| <a name="ltcg"></a>LTCG | 類型 | 活動 |
|  | Parents | [PASS1.LOG](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | 說明 | 發生于連結階段程式碼產生的開始和停止時。 |
| <a name="obj-output"></a>OBJ_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [編譯器](#compiler) |
|  | Children | 無 |
|  | 屬性 | - *.Obj*輸出檔的絕對路徑 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | 說明 | *cl.exe*所產生的每個 *.obj*輸出發生一次。 |
| <a name="opt-icf"></a>OPT_ICF | 類型 | 活動 |
|  | Parents | [PASS1.LOG](#pass1) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | 說明 | 發生于相同的 COMDAT 折迭（/OPT： ICF）連結器優化的開始和停止。 |
| <a name="opt-lbr"></a>OPT_LBR | 類型 | 活動 |
|  | Parents | [PASS1.LOG](#pass1) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | 說明 | 在長分支（/OPT： LBR）連結器優化的啟動和停止時發生。 |
| <a name="opt-ref"></a>OPT_REF | 類型 | 活動 |
|  | Parents | [PASS1.LOG](#pass1) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | 說明 | 在未參考的函式和資料刪除（/OPT： REF）連結器優化的開始和停止時發生。 |
| <a name="pass1"></a>PASS1.LOG | 類型 | 活動 |
|  | Parents | [連結器](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | 說明 | 發生在連結器的開始和停止階段1時。 |
| <a name="pass2"></a>PASS2 | 類型 | 活動 |
|  | Parents | [連結器](#linker) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | 說明 | 發生于連結器的 pass 2 的啟動和停止時。 |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | 類型 | 活動 |
|  | Parents | [PASS1.LOG](#pass1) |
|  | Children | 無 |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | 說明 | 發生在連結器優化階段啟動和停止時，會排除未參考的函式和資料（/OPT： REF）。 這是在連結階段程式碼產生之前完成的。 |
| <a name="symbol-name"></a>SYMBOL_NAME | 類型 | 簡單事件 |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | 無 |
|  | 屬性 | -類型索引鍵<br/> -類型的名稱 |
|  | Capture 類別 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | 說明 | 在前端行程結束時發生：每個包含在範本具現化的類型。 索引鍵是類型的數值識別碼，而名稱則是其文字表示。 類型索引鍵在要分析的追蹤內是唯一的。 不過，來自不同編譯器前端傳遞的不同索引鍵可能會指向相同的類型。 比較不同編譯器前端傳遞之間的類型時，需要使用其名稱。 執行所有範本具現化之後，會在編譯器前端階段結束時發出 SYMBOL_NAME 事件。 |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | 類型 | 活動 |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | -特製化類型的索引鍵<br/>-主要範本類型的索引鍵<br/>-已具現化的範本類型 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | 說明 | 發生在範本具現化的開頭和結尾。 主要的範本類型（例如 `vector` ）會具現化，產生特殊類型（例如 `std::vector<int>` ）。 這兩種類型都會提供一個索引鍵。 使用[SYMBOL_NAME](#symbol-name)事件，將索引鍵轉換為類型的名稱。 類型索引鍵在要分析的追蹤內是唯一的。 不過，來自不同編譯器前端傳遞的不同索引鍵可能會指向相同的類型。 比較不同編譯器前端傳遞之間的類型需要使用符號名稱。 這個事件是遞迴的。 當前端是具現化的嵌套範本時，就會發生遞迴。 |
| <a name="thread"></a>執行緒 | 類型 | 活動 |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [函數](#function) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[執行緒](cpp-event-data-types/thread.md) |
|  | 說明 | 在編譯器後端執行緒執行的開始和結束時發生。 已暫止的執行緒被視為已結束。 正在喚醒的執行緒會被視為已啟動。 |
| <a name="top-down"></a>TOP_DOWN | 類型 | 活動 |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [函數](#function)<br/>[執行緒](#thread) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | 說明 | 在整個程式分析「由上而下」階段開始和停止時發生。 |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | 類型 | 活動 |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | 屬性 | 無 |
|  | Capture 類別 | [活動](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | 說明 | 在連結階段程式碼產生的整個程式分析階段開始和停止時發生。 |

::: moniker-end

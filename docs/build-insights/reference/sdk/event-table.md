---
title: C++產生見解 SDK:事件表
description: 視覺化工作室C++構建見解 SDK 的事件參考
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324151"
---
# <a name="c-build-insights-sdk-event-table"></a>C++產生見解 SDK:事件表

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>編譯器事件

[編譯 器](#compiler)\
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

## <a name="compiler-back-end-events"></a>編譯器後端介面

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[執行緒](#thread)\
[功能](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>連結器事件

[連線](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[通過1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>事件表

| 事件 | 屬性 | 描述 |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | 類型 | 活動 |
|  | Parents | [編譯 器](#compiler) |
|  | Children | [C2_DLL](#c2-dll) |
|  | 屬性 | - 輸入來源的絕對路徑<br/>- 輸出物件檔案的絕對路徑 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[編譯器通行證](cpp-event-data-types/compiler-pass.md)<br/>[後端通行證](cpp-event-data-types/back-end-pass.md) |
|  | 描述 | 發生在編譯器後端傳遞的開始和結束處。 此通道負責優化解析的 C/C++原始碼並將其轉換為機器代碼。 |
| <a name="bottom-up"></a>BOTTOM_UP | 類型 | 活動 |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[自下而上](cpp-event-data-types/bottom-up.md) |
|  | 描述 | 發生在整個程式分析自下而上的開始和結束。 |
| <a name="c1-dll"></a>C1_DLL | 類型 | 活動 |
|  | Parents | [FRONT_END_PASS](#front-end-pass) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | 描述 | 發生在*c1.dll 或 c1xx.dll*調用的開始*c1xx.dll*和結束處。 這些 DLL 是編譯器的 C 和 C++前端。 它們僅由編譯器驅動程式 *(cl.exe)* 調用。 |
| <a name="c2-dll"></a>C2_DLL | 類型 | 活動 |
|  | Parents | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | Children | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | 描述 | 發生在*c2.dll*調用的開始和停止處。 此 DLL 是編譯器的後端介面。 它由編譯器驅動程式 *(cl.exe)* 調用。 使用連結時間代碼生成時,連結器 *(link.exe)* 也會調用它。 |
| <a name="code-generation"></a>CODE_GENERATION | 類型 | 活動 |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [功能](#function)<br/>[執行緒](#thread) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[代碼產生](cpp-event-data-types/code-generation.md) |
|  | 描述 | 發生在後端程式碼生成階段的開始和停止處。 |
| <a name="command-line"></a>COMMAND_LINE | 類型 | 簡單事件 |
|  | Parents | [編譯 器](#compiler)<br/>[連線](#linker) |
|  | Children | None |
|  | 屬性 | - 用於呼叫*cl.exe*或*link.exe*的指令列 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[命令列](cpp-event-data-types/command-line.md) |
|  | 描述 | 當編譯器和連結器完成計算命令行時發生。 評估的命令列包括透過回應檔傳遞的所有*cl.exe*和*link.exe*參數。 它還包括透過環境變數(如 CL、CL、LINK\_\_和\_\_LINK )傳遞的到*cl.exe*和*link.exe*的參數。 |
| <a name="compiler"></a>編譯 器 | 類型 | 活動 |
|  | Parents | None |
|  | Children | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | 屬性 | - 編譯器版本<br/>- 工作目錄<br/>- 被呼叫*的 cl.exe*的絕對路徑 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[引動過程](cpp-event-data-types/invocation.md)<br/>[編譯器](cpp-event-data-types/compiler.md) |
|  | 描述 | 發生在*cl.exe*調用的開頭和停止處。 |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | 類型 | 簡單事件 |
|  | Parents | [編譯 器](#compiler)<br/>[連線](#linker) |
|  | Children | None |
|  | 屬性 | - 環境變數的名稱<br/>- 環境變數的值。 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | 描述 | 在調用*cl.exe*或*link.exe*時,每個現有環境變數發生一次。 |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連線](#linker) |
|  | Children | None |
|  | 屬性 | - DLL 或可執行輸出檔的絕對路徑。 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸出](cpp-event-data-types/file-output.md)<br/>[可執行影像輸出](cpp-event-data-types/executable-image-output.md) |
|  | 描述 | 當其中一個連結器輸入是 DLL 或可執行映像檔時發生。 |
| <a name="exp-output"></a>EXP_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連線](#linker) |
|  | Children | None |
|  | 屬性 | - *.exp*輸出檔的絕對路徑。 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸出](cpp-event-data-types/file-output.md)<br/>[Exp輸出](cpp-event-data-types/exp-output.md) |
|  | 描述 | 當其中一個連結器輸出是 *.exp*檔時發生。 |
| <a name="file-input"></a>FILE_INPUT | 類型 | 簡單事件 |
|  | Parents | [編譯 器](#compiler)<br/>[連線](#linker) |
|  | Children | None |
|  | 屬性 | - 輸入檔案的絕對路徑<br/>- 輸入檔案的類型 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸入](cpp-event-data-types/file-input.md) |
|  | 描述 | 發生以宣佈*cl.exe*或*link.exe*輸入的情況。 |
| <a name="force-inlinee"></a>FORCE_INLINEE | 類型 | 簡單事件 |
|  | Parents | [功能](#function) |
|  | Children | None |
|  | 屬性 | - 力內聯函數的名稱。<br/>- 力內聯函數的大小,表示為中間指令計數。 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[力因內](cpp-event-data-types/force-inlinee.md) |
|  | 描述 | 當函數透過關鍵字強制內聯到另一個函數中時發生`__forceinline`。 |
| <a name="front-end-file"></a>FRONT_END_FILE | 類型 | 活動 |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | Children | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | - 檔案的絕對路徑。 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[前端檔案](cpp-event-data-types/front-end-file.md) |
|  | 描述 | 當編譯器前端啟動並停止處理檔時發生。 此事件是遞歸的。 當前端正在分析包含的檔時,就會發生遞歸。 |
| <a name="front-end-pass"></a>FRONT_END_PASS | 類型 | 活動 |
|  | Parents | [編譯 器](#compiler) |
|  | Children | [C1_DLL](#c1-dll) |
|  | 屬性 | - 輸入來源的絕對路徑<br/>- 輸出物件檔案的絕對路徑 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[編譯器通行證](cpp-event-data-types/compiler-pass.md)<br/>[前端通票](cpp-event-data-types/front-end-pass.md) |
|  | 描述 | 發生在編譯器前端傳遞的開始和結束處。 此傳遞負責分析 C/C++原始碼並將其轉換為中間語言。 |
| <a name="function"></a>功能 | 類型 | 活動 |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[執行緒](#thread)<br/>[TOP_DOWN](#top-down) |
|  | Children | [FORCE_INLINEE](#force-inlinee) |
|  | 屬性 | - 函數名稱 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[函數](cpp-event-data-types/function.md) |
|  | 描述 | 在啟動和結束生成函數的代碼時發生。 |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連線](#linker) |
|  | Children | None |
|  | 屬性 | - 導入庫輸出檔的絕對路徑。 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸出](cpp-event-data-types/file-output.md)<br/>[ImpLib 輸出](cpp-event-data-types/imp-lib-output.md) |
|  | 描述 | 當連結器的一個輸出是導入庫時,就會發生。 |
| <a name="lib-output"></a>LIB_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [連線](#linker) |
|  | Children | None |
|  | 屬性 | - 靜態庫輸出檔的絕對路徑。 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸出](cpp-event-data-types/file-output.md)<br/>[Lib輸出](cpp-event-data-types/lib-output.md) |
|  | 描述 | 當連結器的一個輸出是靜態庫時發生。 |
| <a name="linker"></a>連線 | 類型 | 活動 |
|  | Parents | None |
|  | Children | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[通過1](#pass1)<br/>[PASS2](#pass2) |
|  | 屬性 | - 連結器版本<br/>- 工作目錄<br/>- 呼叫*的連結的絕對路徑. exe* |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[引動過程](cpp-event-data-types/invocation.md)<br/>[連結器](cpp-event-data-types/linker.md) |
|  | 描述 | 在*鏈接*的開頭和停止時發生。 |
| <a name="ltcg"></a>LTCG | 類型 | 活動 |
|  | Parents | [通過1](#pass1) |
|  | Children | [C2_DLL](#c2-dll) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | 描述 | 在鏈接時間代碼生成的開始和停止處發生。 |
| <a name="obj-output"></a>OBJ_OUTPUT | 類型 | 簡單事件 |
|  | Parents | [編譯 器](#compiler) |
|  | Children | None |
|  | 屬性 | - *.obj*輸出檔案的絕對路徑 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[檔案輸出](cpp-event-data-types/file-output.md)<br/>[Obj輸出](cpp-event-data-types/obj-output.md) |
|  | 描述 | 對於*cl.exe*生成的每個 *.obj*輸出發生一次。 |
| <a name="opt-icf"></a>OPT_ICF | 類型 | 活動 |
|  | Parents | [通過1](#pass1) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | 描述 | 在相同的 COMDAT 折疊 (/OPT:ICF) 連結器優化的開始和結束處發生。 |
| <a name="opt-lbr"></a>OPT_LBR | 類型 | 活動 |
|  | Parents | [通過1](#pass1) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | 描述 | 在長分支 (/OPT:LBR) 連結器優化的開始和結束處發生。 |
| <a name="opt-ref"></a>OPT_REF | 類型 | 活動 |
|  | Parents | [通過1](#pass1) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | 描述 | 在未引用函數和資料消除 (/OPT:REF) 連結器優化的開始和停止處發生。 |
| <a name="pass1"></a>通過1 | 類型 | 活動 |
|  | Parents | [連線](#linker) |
|  | Children | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[通行證1](cpp-event-data-types/pass1.md) |
|  | 描述 | 發生在連結器通過 1 的開始和結束處。 |
| <a name="pass2"></a>PASS2 | 類型 | 活動 |
|  | Parents | [連線](#linker) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[通行證2](cpp-event-data-types/pass2.md) |
|  | 描述 | 發生在連結器通過 2 的開始和結束處。 |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | 類型 | 活動 |
|  | Parents | [通過1](#pass1) |
|  | Children | None |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[前LTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | 描述 | 在鏈接器優化傳遞的開始和停止處發生,該傳遞消除了未引用的函數和數據 (/OPT:REF)。 它在連結時間代碼生成之前完成。 |
| <a name="symbol-name"></a>SYMBOL_NAME | 類型 | 簡單事件 |
|  | Parents | [C1_DLL](#c1-dll) |
|  | Children | None |
|  | 屬性 | - 類型鍵<br/> - 類型的名稱 |
|  | 捕獲類 | [簡單事件](cpp-event-data-types/simple-event.md)<br/>[符號名稱](cpp-event-data-types/symbol-name.md) |
|  | 描述 | 發生在前端傳遞的末尾:範本實例化中涉及的每一種類型一次。 鍵是類型的數字標識符,而名稱是其文本表示形式。 類型鍵在要分析的跟蹤中是唯一的。 但是,來自不同編譯器前端傳遞的不同鍵可能指向同一類型。 比較不同編譯器前端傳遞之間的類型需要使用它們的名稱。 在進行所有範本實例化後,SYMBOL_NAME在編譯器前端傳遞結束時發出事件。 |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | 類型 | 活動 |
|  | Parents | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | Children | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 屬性 | - 私人類型的鍵<br/>- 主樣本型態的鍵<br/>- 實體化樣本型態 |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[樣本即時性](cpp-event-data-types/template-instantiation.md) |
|  | 描述 | 發生在範本實例化的開始和結束。 將實體化主樣本型態(`vector`如 ),從而生成專用類型(`std::vector<int>`如 )。 為這兩種類型指定一個鍵。 使用[SYMBOL_NAME](#symbol-name)事件將金鑰轉換為類型的名稱。 類型鍵在要分析的跟蹤中是唯一的。 但是,來自不同編譯器前端傳遞的不同鍵可能指向同一類型。 比較不同編譯器前端傳遞之間的類型需要使用符號名稱。 此事件是遞歸的。 在某些情況下,當前端實例化嵌套範本時,會發生遞歸。 |
| <a name="thread"></a>執行緒 | 類型 | 活動 |
|  | Parents | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | Children | [功能](#function) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[執行緒](cpp-event-data-types/thread.md) |
|  | 描述 | 發生在編譯器後端線程執行的開始和結束。 掛起的線程被視為已結束。 正在喚醒的線程被視為已啟動。 |
| <a name="top-down"></a>TOP_DOWN | 類型 | 活動 |
|  | Parents | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | Children | [功能](#function)<br/>[執行緒](#thread) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[自上而下](cpp-event-data-types/top-down.md) |
|  | 描述 | 發生在整個程式分析的自上而下傳遞的開始和停止。 |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | 類型 | 活動 |
|  | Parents | [C2_DLL](#c2-dll) |
|  | Children | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | 屬性 | None |
|  | 捕獲類 | [活動](cpp-event-data-types/activity.md)<br/>[整個程式分析](cpp-event-data-types/whole-program-analysis.md) |
|  | 描述 | 在連結時間代碼生成的整個程式分析階段的開始和結束時發生。 |

::: moniker-end

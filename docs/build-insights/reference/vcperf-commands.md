---
title: '參考: vcperf 指令'
description: 命令行實用程式 vcperf.exe 的引用。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9d3b0a9dbdfe922dc87f91006441e1f65d54c8a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323244"
---
# <a name="reference-vcperf-commands"></a>參考: vcperf 指令

::: moniker range="<=vs-2017"

C++構建見解工具可在 Visual Studio 2019 中使用。 要查看該版本的文檔,請將本文的可視化工作室**版本**選擇器控制項設置為 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range="vs-2019"

本文列出並描述了*vcperf.exe*中可用的命令,以及如何使用它們。

## <a name="commands-to-start-and-stop-traces"></a>開始與停止追蹤的指令

*重要提示:以下命令都需要管理許可權。*

| 選項           | 參數與描述 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 告訴*vcperf.exe*在給定會話名稱下啟動追蹤。 給定計算機上一次只能有一個活動會話。 <br/><br/> 如果指定`/nocpusampling`了該選項 *,vcperf.exe*不會收集 CPU 樣本。 它可以防止在 Windows 性能分析器中使用 CPU 使用率(採樣)視圖,但會使收集的跟蹤變小。 <br/><br/> 開始跟蹤後 *,vcperf.exe*會立即返回。 對於在計算機上運行的所有進程,將系統範圍內收集事件。 這意味著您不需要從與運行*vcperf.exe*的命令提示相同的命令提示生成專案。 例如,可以從可視化工作室構建專案。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 停止由給定會話名稱標識的跟蹤。 在追蹤上運行後處理步驟,以生成 Windows 性能分析器 (WPA) 中可查看的檔。 為獲得最佳查看體驗,請使用包含C++生成見解外接程式的 WPA 版本。 有關詳細資訊,請參閱[開始C++生成見解](/cpp/build-insights/get-started-with-cpp-build-insights)。 參數`<outputFile.etl>`指定儲存輸出檔的位置。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 停止給定會話名稱識別的追蹤,並在指定的輸出檔中寫入原始未處理的數據。 生成的檔不應在 WPA 中查看。 <br/><br/> `/stop`命令中涉及的后處理步驟有時可能很長。 可以使用`/stopnoanalyze`命令 延遲此後處理步驟。 準備好在`/analyze`Windows 性能分析器中生成可查看的檔時,請使用該命令。 |

## <a name="miscellaneous-commands"></a>其他命令

| 選項     | 參數與描述 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | 接受`/stopnoanalyze`指令產生的原始追蹤檔。 在此追蹤上運行後處理步驟,以生成 Windows 性能分析器中可查看的檔。 為獲得最佳查看體驗,請使用包含C++生成見解外接程式的 WPA 版本。 有關詳細資訊,請參閱[開始C++生成見解](/cpp/build-insights/get-started-with-cpp-build-insights)。 |

## <a name="see-also"></a>另請參閱

[開始C++構建見解](/cpp/build-insights/get-started-with-cpp-build-insights)\
[教學:Windows 效能分析器基礎知識](/cpp/build-insights/tutorials/wpa-basics)\
[參考:Windows 效能分析器檢視](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

---
title: C++Build Insights： vcperf .exe 參考
description: 命令列公用程式 vcperf 的參考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 195d115edae9947b39795440894e4f6bf0ee485e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633095"
---
# <a name="c-build-insights-vcperfexe-reference"></a>C++Build Insights： vcperf .exe 參考

::: moniker range="<=vs-2017"

Visual Studio C++ 2019 中提供 Build Insights 工具。 若要查看該版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2019。

::: moniker-end
::: moniker range="vs-2019"

本文列出並描述*vcperf*中可用的命令，以及如何使用它們。

## <a name="commands-to-start-and-stop-traces"></a>用來啟動和停止追蹤的命令

*重要事項：下列命令全都需要系統管理許可權。*

| 選項           | 引數和描述 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 告訴*vcperf*在指定的會話名稱下啟動追蹤。 在指定的電腦上，一次只能有一個作用中的會話。 <br/><br/> 如果指定了 `/nocpusampling` 選項， *vcperf*就不會收集 CPU 樣本。 它會防止在 Windows Performance Analyzer 中使用 [CPU 使用量（取樣）] 視圖，但會讓收集的追蹤變小。 <br/><br/> 啟動追蹤之後， *vcperf*會立即傳回。 系統會針對在電腦上執行的所有進程，收集整個系統的事件。 這表示您不需要從與您用來執行*vcperf*的命令提示字元中建立專案。 例如，您可以從 Visual Studio 建立專案。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 停止指定的會話名稱所識別的追蹤。 在追蹤上執行後置處理步驟，以產生可在 Windows Performance Analyzer （WPA）中查看的檔案。 若要獲得最佳的觀賞體驗，請使用包含C++ Build Insights 增益集的 WPA 版本。 如需詳細資訊，請參閱[開始C++使用組建深入](get-started-with-cpp-build-insights.md)解析。 `<outputFile.etl>` 參數會指定要儲存輸出檔案的位置。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 停止給定會話名稱所識別的追蹤，並將未經處理、未處理的資料寫入指定的輸出檔中。 產生的檔案不應該在 WPA 中查看。 <br/><br/> `/stop` 命令中所牽涉的後置處理步驟有時可能會很長。 您可以使用 `/stopnoanalyze` 命令來延遲這段後置處理步驟。 當您準備好要產生可在 Windows Performance Analyzer 中查看的檔案時，請使用 `/analyze` 命令。 |

## <a name="miscellaneous-commands"></a>其他命令

| 選項     | 引數和描述 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | 接受 `/stopnoanalyze` 命令所產生的原始追蹤檔案。 在此追蹤上執行後置處理步驟，以產生可在 Windows Performance Analyzer 中查看的檔案。 若要獲得最佳的觀賞體驗，請使用包含C++ Build Insights 增益集的 WPA 版本。 如需詳細資訊，請參閱[開始C++使用組建深入](get-started-with-cpp-build-insights.md)解析。 |

## <a name="see-also"></a>請參閱

[開始使用C++ Build Insights](get-started-with-cpp-build-insights.md)\
[Windows Performance Analyzer 基本概念](wpa-basics.md)\
[Windows Performance Analyzer views 參考](wpa-views-reference.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

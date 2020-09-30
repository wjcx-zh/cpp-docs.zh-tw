---
title: 參考： vcperf 命令
description: 命令列公用程式 vcperf.exe 的參考。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c251d93ce7e9e7325a7146f5697150344cb02d96
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508812"
---
# <a name="reference-vcperf-commands"></a>參考： vcperf 命令

::: moniker range="<=vs-2017"

C + + Build Insights 工具可在 Visual Studio 2019 中取得。 若要查看該版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range="vs-2019"

本文列出並描述 *vcperf.exe*中可用的命令，以及如何使用它們。

## <a name="commands-to-start-and-stop-traces"></a>用來啟動和停止追蹤的命令

*重要：下列命令都需要系統管理許可權。*

| 選項           | 引數和描述 |
|------------------|---------------------------|
| `/start`         | `[/nocpusampling]` `<sessionName>` |
|                  | 告知 *vcperf.exe* 在指定的會話名稱下啟動追蹤。 在指定的電腦上一次只能有一個作用中的會話。 <br/><br/> 如果 `/nocpusampling` 指定了選項， *vcperf.exe* 不會收集 CPU 範例。 它會防止在 Windows Performance Analyzer 中 (取樣) 視圖使用 CPU 使用量，但會讓收集的追蹤變得較小。 <br/><br/> 一旦啟動追蹤， *vcperf.exe* 會立即傳回。 系統會針對在電腦上執行的所有進程收集全系統的事件。 這表示您不需要從與用來執行 *vcperf.exe*的相同命令提示字元建立您的專案。 例如，您可以從 Visual Studio 建立您的專案。 |
| `/stop`          | `<sessionName>` `<outputFile.etl>` |
|                  | 停止指定的會話名稱所識別的追蹤。 在追蹤上執行後續處理步驟，以產生可在 Windows Performance Analyzer (WPA) 中查看的檔案。 若要獲得最佳的觀賞體驗，請使用包含 c + + Build Insights 增益集的 WPA 版本。 如需詳細資訊，請參閱 [開始使用 c + + Build Insights](../get-started-with-cpp-build-insights.md)。 `<outputFile.etl>`參數會指定要儲存輸出檔案的位置。 |
| `/stopnoanalyze` | `<sessionName>` `<rawOutputFile.etl>` |
|                  | 停止由指定的會話名稱所識別的追蹤，並將未經處理的未經處理資料寫入指定的輸出檔中。 產生的檔案並不是要在 WPA 中進行查看。 <br/><br/> 命令中的後續處理步驟有時可能 `/stop` 會很長。 您可以使用 `/stopnoanalyze` 命令來延遲此後置處理步驟。 `/analyze`當您準備好要產生可在 Windows Performance Analyzer 中查看的檔案時，請使用命令。 |

## <a name="miscellaneous-commands"></a>其他命令

| 選項     | 引數和描述 |
|------------|---------------------------|
| `/analyze` | `<rawInputFile.etl> <outputFile.etl>` |
|            | 接受命令所產生的原始追蹤檔案 `/stopnoanalyze` 。 在此追蹤上執行後續處理步驟，以產生可在 Windows Performance Analyzer 中查看的檔案。 若要獲得最佳的觀賞體驗，請使用包含 c + + Build Insights 增益集的 WPA 版本。 如需詳細資訊，請參閱 [開始使用 c + + Build Insights](../get-started-with-cpp-build-insights.md)。 |

## <a name="see-also"></a>另請參閱

[開始使用 c + + Build Insights](../get-started-with-cpp-build-insights.md)\
[教學課程： Windows Performance Analyzer 基本概念](../tutorials/wpa-basics.md)\
[參考： Windows Performance Analyzer 視圖](wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end

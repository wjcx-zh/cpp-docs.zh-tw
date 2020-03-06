---
title: AnalysisControl 列舉類別
description: C++ BUILD Insights SDK AnalysisControl 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332499"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl 列舉類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalysisControl` 列舉類別是用來控制分析或 relogging 會話的流程。 從[IAnalyzer](ianalyzer-class.md)或[IRelogger](irelogger-class.md)成員函式傳回 `AnalysisControl` 的程式碼，以控制接下來應發生的動作。

## <a name="members"></a>成員

|  |  |
|--|--|
| `BLOCK` | 防止目前事件在分析器或 relogger 群組中進一步傳播。 |
| `CANCEL` | 取消目前的分析或 relogging 會話。 |
| `CONTINUE` | 繼續正常執行目前的分析或 relogging 會話。 將目前的事件傳播到下一個分析器或 relogger 群組成員。 |
| `FAILURE` | 取消目前的分析或 relogging 會話，併發出錯誤。 |

::: moniker-end

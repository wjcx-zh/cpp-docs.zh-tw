---
title: 分析控制枚舉類
description: C++生成見解 SDK 分析控制枚舉引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323635"
---
# <a name="analysiscontrol-enum-class"></a>分析控制枚舉類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`AnalysisControl`舉類用於控制分析或重新記錄會話的流。 從`AnalysisControl`[IAnalyzer](ianalyzer-class.md)或[IRelogger](irelogger-class.md)成員函數返回代碼,以控制接下來會發生什麼。

## <a name="members"></a>成員

|  |  |
|--|--|
| `BLOCK` | 防止當前事件在分析器或重新記錄組中進一步傳播。 |
| `CANCEL` | 取消當前分析或重新記錄工作階段。 |
| `CONTINUE` | 正常繼續當前分析或重新記錄會話。 將當前事件傳播到下一個分析器或重新記錄組成員。 |
| `FAILURE` | 取消當前分析或重新記錄會話併發出錯誤信號。 |

::: moniker-end

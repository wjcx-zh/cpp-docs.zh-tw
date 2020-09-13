---
title: AnalysisControl 列舉類別
description: C + + Build Insights SDK AnalysisControl 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a7b7fc0ce404f414b3ec07449bdc110d578fa101
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042013"
---
# <a name="analysiscontrol-enum-class"></a>AnalysisControl 列舉類別

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`AnalysisControl`列舉類別是用來控制分析或 relogging 會話的流程。 `AnalysisControl`從[IAnalyzer](ianalyzer-class.md)或[IRelogger](irelogger-class.md)成員函式傳回程序代碼，以控制接下來應進行的動作。

## <a name="members"></a>成員

| 名稱 | 描述 |
|--|--|
| `BLOCK` | 防止目前的事件進一步傳播至分析器或 relogger 群組。 |
| `CANCEL` | 取消目前的分析或 relogging 會話。 |
| `CONTINUE` | 正常繼續目前的分析或 relogging 會話。 將目前的事件傳播至下一個分析器或 relogger 群組成員。 |
| `FAILURE` | 取消目前的分析或 relogging 會話，併發出錯誤通知。 |

::: moniker-end

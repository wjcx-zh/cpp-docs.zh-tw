---
title: CALLBACK_CODE 列舉
description: C++ BUILD Insights SDK CALLBACK_CODE 列舉參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332464"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE 列舉

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`CALLBACK_CODE` 列舉是用來控制分析或 relogging 會話的流程。 從[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)或[RELOG_CALLBACKS](relog-callbacks-struct.md)中的函式傳回 CALLBACK_CODE 值，以控制接下來應該發生的情況。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 繼續正常執行目前的分析或 relogging 會話。 |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2（0x00000002） | 取消目前的分析或 relogging 會話，併發出錯誤。 |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4（0x00000004） | 取消目前的分析或 relogging 會話。 |

::: moniker-end

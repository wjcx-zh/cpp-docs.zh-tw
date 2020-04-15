---
title: CALLBACK_CODE枚舉
description: C++生成見解 SDK CALLBACK_CODE枚舉引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329183"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE枚舉

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

枚`CALLBACK_CODE`舉用於控制分析或重新記錄會話的流。 從[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)或[RELOG_CALLBACKS](relog-callbacks-struct.md)中的函數返回CALLBACK_CODE值,以控制接下來會發生什麼。

## <a name="members"></a>成員

| 名稱 | 值 | 描述 |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | 正常繼續當前分析或重新記錄會話。 |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x0000002) | 取消當前分析或重新記錄會話併發出錯誤信號。 |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x0000004) | 取消當前分析或重新記錄工作階段。 |

::: moniker-end

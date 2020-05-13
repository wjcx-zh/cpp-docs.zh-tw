---
title: INVOCATION_DATA結構
description: C++生成見解 SDK INVOCATION_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325479"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`INVOCATION_DATA`描述編譯器或連結器呼叫。

## <a name="syntax"></a>語法

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `MSVCToolCode` | 標識調用類型的代碼。 有關詳細資訊,請參閱[MSVC_TOOL_CODE](msvc-tool-code-enum.md)。 |
| `ToolVersion` | 將被調用的工具版本存儲為一組積分值的物件。 |
| `ToolVersionString` | 以文本形式描述被調用的工具版本。 |
| `WorkingDirectory` | 調用的目錄。 |
| `ToolPath` | 被調用的工具的絕對路徑。 |

::: moniker-end

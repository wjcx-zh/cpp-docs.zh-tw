---
title: INVOCATION_DATA 結構
description: C++ BUILD Insights SDK INVOCATION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333689"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA` 結構描述編譯器或連結器調用。

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
| `MSVCToolCode` | 識別調用類型的程式碼。 如需詳細資訊，請參閱[MSVC_TOOL_CODE](msvc-tool-code-enum.md)。 |
| `ToolVersion` | 物件，將叫用工具的版本儲存為整數值的群組。 |
| `ToolVersionString` | 描述以文字格式叫用的工具版本。 |
| `WorkingDirectory` | 從中進行調用的目錄。 |
| `ToolPath` | 叫用工具的絕對路徑。 |

::: moniker-end

---
title: INVOCATION_DATA 結構
description: C + + Build Insights SDK INVOCATION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 48b4c28d3c01d61a31343894312a54ba2ab17a70
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041636"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_DATA`結構描述編譯器或連結器調用。

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

| 名稱 | 描述 |
|--|--|
| `MSVCToolCode` | 識別調用型別的程式碼。 如需詳細資訊，請參閱 [MSVC_TOOL_CODE](msvc-tool-code-enum.md)。 |
| `ToolVersion` | 物件，將叫用的工具版本儲存為整數值的群組。 |
| `ToolVersionString` | 描述以文字形式叫用的工具版本。 |
| `WorkingDirectory` | 從中進行調用的目錄。 |
| `ToolPath` | 叫用的工具絕對路徑。 |

::: moniker-end

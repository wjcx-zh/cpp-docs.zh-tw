---
title: FUNCTION_FORCE_INLINEE_DATA 結構
description: C++ BUILD Insights SDK FUNCTION_FORCE_INLINEE_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333696"
---
# <a name="function_force_inlinee_data-structure"></a>FUNCTION_FORCE_INLINEE_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_FORCE_INLINEE_DATA` 結構描述強制內嵌函數。

## <a name="syntax"></a>語法

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Name` | 函式的名稱，以 UTF-8 編碼。 |
| `Size` | 函式的大小，以中繼指示的數目為限。 |

::: moniker-end

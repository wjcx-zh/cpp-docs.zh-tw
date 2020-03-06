---
title: FUNCTION_DATA 結構
description: C++ BUILD Insights SDK FUNCTION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 718e93bed798786a4596ccb3e724b2b54d4fe79d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333731"
---
# <a name="function_data-structure"></a>FUNCTION_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_DATA` 結構描述函數。

## <a name="syntax"></a>語法

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Name` | 函式的名稱，以 UTF-8 編碼。 |

::: moniker-end

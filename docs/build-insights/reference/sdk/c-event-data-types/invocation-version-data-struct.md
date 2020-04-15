---
title: INVOCATION_VERSION_DATA結構
description: C++生成見解 SDK INVOCATION_VERSION_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325476"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`INVOCATION_VERSION_DATA`將版本號描述為一組積分值。

## <a name="syntax"></a>語法

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `VersionMajor` | 版本的主要編號。 |
| `VersionMinor` | 版本的次要編號。 |
| `BuildNumberMajor` | 生成的主要編號。 |
| `BuildNumberMinor` | 生成的小數。 |

::: moniker-end

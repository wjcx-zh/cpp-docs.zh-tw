---
title: INVOCATION_VERSION_DATA 結構
description: C++ BUILD Insights SDK INVOCATION_VERSION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333675"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`INVOCATION_VERSION_DATA` 結構會將版本號碼描述為整數值的群組。

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
| `VersionMajor` | 版本的主要號碼。 |
| `VersionMinor` | 版本的次要號碼。 |
| `BuildNumberMajor` | 組建的主要編號。 |
| `BuildNumberMinor` | 組建的次要編號。 |

::: moniker-end

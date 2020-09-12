---
title: INVOCATION_VERSION_DATA 結構
description: C + + Build Insights SDK INVOCATION_VERSION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ec54c560dd408dc3beecbc20eaac69d389c7ec37
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041555"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

結構會將 `INVOCATION_VERSION_DATA` 版本號碼描述為整數值的群組。

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

| Name | 描述 |
|--|--|
| `VersionMajor` | 版本的主要號碼。 |
| `VersionMinor` | 版本的次要號碼。 |
| `BuildNumberMajor` | 組建的主要數位。 |
| `BuildNumberMinor` | 組建的次要號碼。 |

::: moniker-end

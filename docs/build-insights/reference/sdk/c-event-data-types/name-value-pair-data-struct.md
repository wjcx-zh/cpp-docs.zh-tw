---
title: NAME_VALUE_PAIR_DATA 結構
description: C++ BUILD Insights SDK NAME_VALUE_PAIR_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6c4f6fef11e6365bdc930d5df1f48f72186ebdb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333640"
---
# <a name="name_value_pair_data-structure"></a>NAME_VALUE_PAIR_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`NAME_VALUE_PAIR_DATA` 結構描述名稱和值配對。

## <a name="syntax"></a>語法

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Name` | 名稱 |
| `Value` | 值。 |

::: moniker-end

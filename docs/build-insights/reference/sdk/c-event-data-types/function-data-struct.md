---
title: FUNCTION_DATA 結構
description: C + + Build Insights SDK FUNCTION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1034ce01bba6422d0c47fc34b308cafcc113e32b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041740"
---
# <a name="function_data-structure"></a>FUNCTION_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`FUNCTION_DATA`結構描述函數。

## <a name="syntax"></a>語法

```cpp
typedef struct FUNCTION_DATA_TAG
{
    const char*         Name;

} FUNCTION_DATA;
```

## <a name="members"></a>成員

| 名稱 | 描述 |
|--|--|
| `Name` | 函數的名稱，以 UTF-8 編碼。 |

::: moniker-end

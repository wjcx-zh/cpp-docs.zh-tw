---
title: SYMBOL_NAME_DATA 結構
description: C + + Build Insights SDK SYMBOL_NAME_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d234c6c225eff87a0eecd98fa5ff60bf92db97f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041909"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`SYMBOL_NAME_DATA`結構描述編譯器前端符號。

## <a name="syntax"></a>語法

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>成員

| Name | 描述 |
|--|--|
| `Key` | 符號的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `Name` | 符號的名稱。 |

## <a name="remarks"></a>備註

來自兩個不同編譯器前端傳遞的符號，可能會有相同的名稱，但不同的索引鍵。 在此情況下，請使用符號名稱來判斷兩個類型是否相同。

::: moniker-end

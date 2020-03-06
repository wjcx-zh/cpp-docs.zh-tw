---
title: SYMBOL_NAME_DATA 結構
description: C++ BUILD Insights SDK SYMBOL_NAME_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 618e84f198c20aa089dc7e06e1e6c09b96b6d273
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333633"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`SYMBOL_NAME_DATA` 結構描述編譯器前端符號。

## <a name="syntax"></a>語法

```cpp
typedef struct SYMBOL_NAME_DATA_TAG
{
    unsigned long long  Key;
    const char*         Name;

} SYMBOL_NAME_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Key` | 符號的索引鍵。 這個值在要分析的追蹤內是唯一的。 |
| `Name` | 符號的名稱。 |

## <a name="remarks"></a>備註

來自兩個不同編譯器前端傳遞的符號可能具有相同的名稱，但具有不同的索引鍵。 在此情況下，請使用符號名稱來判斷兩個類型是否相同。

::: moniker-end

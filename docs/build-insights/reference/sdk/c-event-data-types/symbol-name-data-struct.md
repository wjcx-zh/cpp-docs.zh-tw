---
title: SYMBOL_NAME_DATA結構
description: C++生成見解 SDK SYMBOL_NAME_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SYMBOL_NAME_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1217572f20a772fde629533d6ab170c14dc5b5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325343"
---
# <a name="symbol_name_data-structure"></a>SYMBOL_NAME_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`SYMBOL_NAME_DATA`描述編譯器前端符號。

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
| `Key` | 符號的鍵。 此值在要分析的跟蹤中是唯一的。 |
| `Name` | 符號的名稱。 |

## <a name="remarks"></a>備註

來自兩個不同的編譯器前端傳遞的符號可能具有相同的名稱,但密鑰不同。 在這種情況下,使用符號名稱確定兩種類型是否相同。

::: moniker-end

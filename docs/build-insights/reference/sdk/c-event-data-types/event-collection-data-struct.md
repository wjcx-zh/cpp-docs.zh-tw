---
title: EVENT_COLLECTION_DATA結構
description: C++構建見解 SDK EVENT_COLLECTION_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325697"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`EVENT_COLLECTION_DATA`結構描述了[EVENT_DATA](event-data-struct.md)元素的陣組。

## <a name="syntax"></a>語法

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Count` | 陣列中的元素`EVENT_DATA`數。 |
| `Elements` | 指向陣列中的第`EVENT_DATA`一個元素。 |

::: moniker-end

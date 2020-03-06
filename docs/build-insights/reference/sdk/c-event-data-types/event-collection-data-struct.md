---
title: EVENT_COLLECTION_DATA 結構
description: C++ BUILD Insights SDK EVENT_COLLECTION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1a622a8459b6aa6d9dcbe0faaf90ae545b449466
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333808"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_COLLECTION_DATA` 結構描述[EVENT_DATA](event-data-struct.md)元素的陣列。

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
| `Count` | 陣列中的 `EVENT_DATA` 元素數目。 |
| `Elements` | 陣列中第一個 `EVENT_DATA` 元素的指標。 |

::: moniker-end

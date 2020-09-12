---
title: EVENT_COLLECTION_DATA 結構
description: C + + Build Insights SDK EVENT_COLLECTION_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 58be46d31af154bfe7ecef5c440092eaafdcbb0f
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039595"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_COLLECTION_DATA`結構描述[EVENT_DATA](event-data-struct.md)元素的陣列。

## <a name="syntax"></a>語法

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>成員

| Name | 描述 |
|--|--|
| `Count` | `EVENT_DATA`陣列中的元素數目。 |
| `Elements` | 陣列中第一個 `EVENT_DATA` 元素的指標。 |

::: moniker-end

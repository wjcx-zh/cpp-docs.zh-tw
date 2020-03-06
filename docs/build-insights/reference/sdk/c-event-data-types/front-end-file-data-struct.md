---
title: FRONT_END_FILE_DATA 結構
description: C++ BUILD Insights SDK FRONT_END_FILE_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FRONT_END_FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 33232a0f83566e58e64964e84961a7ade2de7b7c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333738"
---
# <a name="front_end_file_data-structure"></a>FRONT_END_FILE_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FRONT_END_FILE_DATA` 結構描述編譯器前端處理檔案的方式。

## <a name="syntax"></a>語法

```cpp
typedef struct FRONT_END_FILE_DATA_TAG
{
    const char*         Path;

} FRONT_END_FILE_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Path` | 檔案的絕對路徑，以 UTF-8 編碼。 |

::: moniker-end

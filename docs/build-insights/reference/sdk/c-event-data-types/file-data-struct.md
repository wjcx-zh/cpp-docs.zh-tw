---
title: FILE_DATA 結構
description: C++ BUILD Insights SDK FILE_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 72cae8c8eb81bdb8d94897c46c5af90c89e92ab4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333752"
---
# <a name="file_data-structure"></a>FILE_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_DATA` 結構描述檔案輸入或輸出。

## <a name="syntax"></a>語法

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `Path` | 檔案的絕對路徑 |
| `TypeCode` | 描述檔案類型的程式碼。 如需詳細資訊，請參閱[FILE_TYPE_CODE](file-type-code-enum.md)。 |

::: moniker-end

---
title: FILE_DATA 結構
description: C + + Build Insights SDK FILE_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FILE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5f793df0340005665a8f4ab42e9793f51f3aa0c
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041805"
---
# <a name="file_data-structure"></a>FILE_DATA 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`FILE_DATA`結構描述檔案的輸入或輸出。

## <a name="syntax"></a>語法

```cpp
typedef struct FILE_DATA_TAG
{
    const wchar_t*      Path;
    int                 TypeCode;

} FILE_DATA;
```

## <a name="members"></a>成員

| Name | 描述 |
|--|--|
| `Path` | 檔案的絕對路徑 |
| `TypeCode` | 描述檔案類型的程式碼。 如需詳細資訊，請參閱 [FILE_TYPE_CODE](file-type-code-enum.md)。 |

::: moniker-end

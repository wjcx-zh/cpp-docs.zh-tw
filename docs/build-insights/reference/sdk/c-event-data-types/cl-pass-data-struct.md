---
title: CL_PASS_DATA 結構
description: C++ BUILD Insights SDK CL_PASS_DATA 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333822"
---
# <a name="cl_pass_data-structure"></a>CL_PASS_DATA 結構

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`CL_PASS_DATA` 結構描述編譯階段。

## <a name="syntax"></a>語法

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `TranslationUnitPassCode` | 識別正在執行之編譯階段的程式碼。 如需詳細資訊，請參閱[TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md)。 |
| `InputSourcePath` | 執行此編譯C++階段的 C 或來源檔案。 |
| `OutputObjectPath` | 編譯器所產生的物件檔案。 |

::: moniker-end

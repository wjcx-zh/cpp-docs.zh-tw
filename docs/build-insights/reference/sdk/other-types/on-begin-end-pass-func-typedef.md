---
title: OnBeginEndPassFunc typedef
description: C++ BUILD Insights SDK OnBeginEndPassFunc typedef 參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnBeginEndPassFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6f5e602fdc460acf8e53307e88a1a3d7ad000893
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332422"
---
# <a name="onbeginendpassfunc-typedef"></a>OnBeginEndPassFunc typedef

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`OnBeginEndPassFunc` typedef 是[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)和[RELOG_CALLBACKS](relog-callbacks-struct.md)結構中所使用的其中一個函式簽章。

## <a name="syntax"></a>語法

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnBeginEndPassFunc)(
    void*                           callbackContext);
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `callbackContext` |  |

::: moniker-end

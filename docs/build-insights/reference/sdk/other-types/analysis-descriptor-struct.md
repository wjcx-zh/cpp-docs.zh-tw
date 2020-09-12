---
title: ANALYSIS_DESCRIPTOR 結構
description: C + + Build Insights SDK ANALYSIS_DESCRIPTOR 結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 325910f747f75f1f8d2904c248f8de69566464c7
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042000"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR 結構

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

此 `ANALYSIS_DESCRIPTOR` 結構會搭配 [AnalyzeA](../functions/analyze-a.md) 和 [AnalyzeW](../functions/analyze-w.md) 函數使用。 說明如何分析 Windows (ETW) 追蹤的事件追蹤。

## <a name="syntax"></a>語法

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>成員

| Name | 描述 |
|--|--|
| `NumberOfPasses` | 應透過 ETW 追蹤完成的分析傳遞數目。 |
| `Callbacks` | [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)物件，指定要在分析會話期間呼叫的函式。 |
| `Context` | 使用者提供的內容，此內容會作為引數傳遞至指定的所有回呼函數 `Callbacks` |

## <a name="remarks"></a>備註

`Callbacks`結構只接受非成員函式的指標。 您可以藉由設定 `Context` 為物件指標來解決這項限制。 此物件指標會以引數的形式傳遞給您所有的非成員回呼函數。 使用這個指標可從您的非成員回呼函數中呼叫成員函式。

::: moniker-end

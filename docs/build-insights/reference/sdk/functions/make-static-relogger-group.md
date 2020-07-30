---
title: MakeStaticReloggerGroup
description: C + + Build Insights SDK MakeStaticReloggerGroup 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b74ee778ffafbcb4c292b4b36b309d5ff4d66c27
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224158"
---
# <a name="makestaticreloggergroup"></a>MakeStaticReloggerGroup

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

函式 `MakeStaticReloggerGroup` 可用來建立可以傳遞至函式（如重新[引發）的](relog.md)靜態 relogger 群組。 Relogger 群組的成員會從左至右接收事件，直到追蹤中的所有事件都已處理為止。

## <a name="syntax"></a>語法

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>參數

*TReloggerPtrs*\
這個參數一律會推算。

*reloggers*\
[`IRelogger`](../other-types/irelogger-class.md)靜態 relogger 群組中所包含之指標的參數套件。 這些指標可以是原始、 `std::unique_ptr` 或 `std::shared_ptr` 。 [`IAnalyzer`](../other-types/ianalyzer-class.md)指標也會被視為 `IRelogger` 指標，因為繼承關聯性。

### <a name="return-value"></a>傳回值

靜態 relogger 群組。 使用 **`auto`** 關鍵字來捕捉傳回值。

## <a name="remarks"></a>備註

不同于動態 relogger 群組，靜態 relogger 群組的成員在編譯時期必須是已知的。 此外，靜態 relogger 群組包含沒有多型 [`IRelogger`](../other-types/irelogger-class.md) 行為的指標。 使用靜態 relogger 群組分析 Windows 事件追蹤（ETW）追蹤時，對介面的呼叫 `IRelogger` 一律會解析為 relogger 群組成員直接指向的物件。 這樣的彈性可能會導致事件處理時間更快。 如果 relogger 群組的成員在編譯時期無法得知，或如果您在指標上需要多型行為 `IRelogger` ，請考慮使用動態 relogger 群組。 您可以改為呼叫來使用動態 relogger 群組 [`MakeDynamicReloggerGroup`](make-dynamic-relogger-group.md) 。

::: moniker-end

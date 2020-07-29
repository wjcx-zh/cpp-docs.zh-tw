---
title: MakeDynamicReloggerGroup
description: C + + Build Insights SDK MakeDynamicReloggerGroup 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c0d1348be8878e686aeba4a58c407264264c5bc4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224184"
---
# <a name="makedynamicreloggergroup"></a>MakeDynamicReloggerGroup

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`MakeDynamicReloggerGroup`函數是用來建立動態 relogger 群組。 Relogger 群組的成員會從左至右接收事件，直到追蹤中的所有事件都已處理為止。

## <a name="syntax"></a>語法

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>參數

*reloggers*\
包含在動態 relogger 群組中的[IRelogger](../other-types/irelogger-class.md)指標向量。 這些指標可以是原始、 `std::unique_ptr` 或 `std::shared_ptr` 。 [IAnalyzer](../other-types/ianalyzer-class.md)指標也會被視為 `IRelogger` 指標，因為繼承關聯性。

### <a name="return-value"></a>傳回值

動態 relogger 群組。 使用 **`auto`** 關鍵字來捕捉傳回值。

## <a name="remarks"></a>備註

不同于靜態 relogger 群組，dynamic relogger 群組的成員在編譯時期不需要知道。 您可以根據程式輸入，或根據在編譯時期未知的其他值，在執行時間選擇 relogger 群組成員。 不同于靜態 relogger 群組， [`IRelogger`](../other-types/irelogger-class.md) 動態 relogger 群組內的指標具有多型行為，而且會正確分派虛擬函式呼叫。 這項彈性的代價是，事件處理時間可能較慢。 當所有 relogger 群組成員都在編譯階段為已知時，如果您不需要多型行為，請考慮使用靜態 relogger 群組。 若要使用靜態 relogger 群組，請 [`MakeStaticReloggerGroup`](make-static-relogger-group.md) 改為呼叫。

動態 relogger 群組可以封裝在靜態 relogger 群組內。 您會將其位址傳遞給 [`MakeStaticReloggerGroup`](make-static-relogger-group.md) 。 使用這項技術，將動態 relogger 群組傳遞至 [`Relog`](relog.md) 僅接受靜態 relogger 群組的函數（例如）。

::: moniker-end

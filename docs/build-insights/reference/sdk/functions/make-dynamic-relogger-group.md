---
title: 將動態重新記錄群組
description: C++生成見解 SDK 使動態重新記錄組函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeDynamicReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f49e37f8e1a8b9ca9a800d20b2891a54453095ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323944"
---
# <a name="makedynamicreloggergroup"></a>將動態重新記錄群組

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MakeDynamicReloggerGroup`函數用於創建動態重新記錄組。 重新記錄組的成員從左到右逐個接收事件,直到跟蹤中的所有事件都得到處理。

## <a name="syntax"></a>語法

```cpp
auto MakeDynamicReloggerGroup(std::vector<IRelogger*> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::shared_ptr<IRelogger>> reloggers);

auto MakeDynamicReloggerGroup(std::vector<std::unique_ptr<IRelogger>> reloggers);
```

### <a name="parameters"></a>參數

*重新記錄*\
動態[重新記錄組中包含的 IRelogger](../other-types/irelogger-class.md)指標的向量。 這些指標可以是生的,`std::unique_ptr`也可以`std::shared_ptr`是 。 [由於繼承關係,IAnalyzer](../other-types/ianalyzer-class.md)指標也被視為`IRelogger`指標。

### <a name="return-value"></a>傳回值

動態重新記錄組。 使用**自動**關鍵字捕獲返回值。

## <a name="remarks"></a>備註

與靜態重新記錄組不同,動態重新記錄組的成員不需要在編譯時已知。 您可以根據程式輸入或在執行時根據編譯時未知的其他值選擇重新記錄組成員。 與靜態重新記錄器組不同,動態重新記錄器組中的[IRelogger](../other-types/irelogger-class.md)指標具有多態行為,並且虛擬函數調用正確調度。 這種靈活性的代價可能是較慢的事件處理時間。 當所有重新記錄組成員在編譯時都已知,並且不需要多態行為時,請考慮使用靜態重新記錄組。 要使用靜態重新記錄組,請改為調用[MakeStaticReloggerGroup。](make-static-relogger-group.md)

動態重新記錄器組可以封裝在靜態重新記錄器組中。 您可以透過它的位址[,讓靜態重新紀錄群組](make-static-relogger-group.md)。 使用此技術將動態重新記錄器組傳遞給函數,如[Relog](relog.md),該函數僅接受靜態重新記錄組。

::: moniker-end

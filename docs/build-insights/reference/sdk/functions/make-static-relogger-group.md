---
title: 將靜態重新記錄群組
description: C++生成見解 SDK 使靜態重新記錄組函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MakeStaticReloggerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 75b638537cb8e0cdeeb5476a3f5277e8e90d9baf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323905"
---
# <a name="makestaticreloggergroup"></a>將靜態重新記錄群組

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

此`MakeStaticReloggerGroup`函數用於建立一個靜態重新記錄組,該組可以傳遞給函數,如[Relog](relog.md)。 重新記錄組的成員從左到右逐個接收事件,直到跟蹤中的所有事件都得到處理。

## <a name="syntax"></a>語法

```cpp
template <typename... TReloggerPtrs>
auto MakeStaticReloggerGroup(TReloggerPtrs... reloggers);
```

### <a name="parameters"></a>參數

*TReloggerPtrs*\
始終推導此參數。

*重新記錄*\
包含在靜態重新記錄器組中的[IRelogger](../other-types/irelogger-class.md)指標的參數包。 這些指標可以是生的,`std::unique_ptr`也可以`std::shared_ptr`是 。 [由於繼承關係,IAnalyzer](../other-types/ianalyzer-class.md)指標也被視為`IRelogger`指標。

### <a name="return-value"></a>傳回值

靜態重新記錄組。 使用**自動**關鍵字捕獲返回值。

## <a name="remarks"></a>備註

與動態重新記錄組不同,靜態重新記錄組的成員必須在編譯時知道。 此外,靜態重新記錄器組包含沒有多態行為的[IRelogger](../other-types/irelogger-class.md)指標。 當使用靜態重新記錄組分析 Windows (ETW) 追蹤的事件追蹤時,`IRelogger`對介面的調用始終解析為重新記錄組成員直接指向的物件。 這種靈活性的喪失具有更快的事件處理時間的可能性。 如果在編譯時無法知道重新記錄組的成員,或者在`IRelogger`指標上需要多態行為,請考慮使用動態重新記錄組。 您可以通過調用[MakeDynamic ReloggerGroup](make-dynamic-relogger-group.md)來使用動態重新記錄組。

::: moniker-end

---
title: ImpLib 輸出類別
description: C++生成見解 SDK ImpLibOutput 類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 98905dfe75484e98e14a0fa575e75fe3ab284559
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324706"
---
# <a name="impliboutput-class"></a>ImpLib 輸出類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`ImpLibOutput`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)事件。

## <a name="syntax"></a>語法

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了從[FileOutput](file-output.md)基類別繼承的成員一`ImpLibOutput`起, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[ImpLib 輸出](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a>ImpLib 輸出

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[IMP_LIB_OUTPUT](../event-table.md#imp-lib-output)事件。

::: moniker-end

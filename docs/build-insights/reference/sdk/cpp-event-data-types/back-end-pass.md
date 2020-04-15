---
title: 後端傳遞類
description: C++生成見解 SDK 後端傳遞類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b4b1a219abdbe418efaab4537f1c6dc9a22afb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325231"
---
# <a name="backendpass-class"></a>後端傳遞類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`BackEndPass`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[BACK_END_PASS](../event-table.md#back-end-pass)事件。

## <a name="syntax"></a>語法

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了從[其編譯器Pass](compiler-pass.md)基類繼承的成員一`BackEndPass`起, 該類包含以下成員:

### <a name="constructors"></a>建構函式

[後端通行證](#back-end-pass)

## <a name="backendpass"></a><a name="back-end-pass"></a>後端通行證

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[BACK_END_PASS](../event-table.md#back-end-pass)事件。

::: moniker-end

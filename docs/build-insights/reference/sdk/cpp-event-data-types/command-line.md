---
title: 命令列類
description: C++生成見解 SDK 命令行類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325053"
---
# <a name="commandline-class"></a>命令列類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`CommandLine`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="syntax"></a>語法

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>成員

除了其[SimpleEvent](simple-event.md)基類別中繼承的成員`CommandLine`外, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[命令列](#command-line)

### <a name="functions"></a>函式

[ReplTest1](#value)

## <a name="commandline"></a><a name="command-line"></a>命令列

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="value"></a><a name="value"></a> 值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>傳回值

引入命令列的字串。 該值\_包括從回應檔和環境變數(如\_CL、CL、Link\_和\_LINK )獲取的參數。

::: moniker-end

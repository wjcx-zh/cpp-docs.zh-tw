---
title: 命令列類別
description: C++ BUILD Insights SDK 命令列類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333507"
---
# <a name="commandline-class"></a>命令列類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`CommandLine` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[COMMAND_LINE](../event-table.md#command-line)事件。

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

除了來自其[SimpleEvent](simple-event.md)基類的繼承成員之外，`CommandLine` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[命令列](#command-line)

### <a name="functions"></a>Functions

[ReplTest1](#value)

## <a name="command-line"></a>命令列

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[COMMAND_LINE](../event-table.md#command-line)事件。

## <a name="value"></a>Value

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>傳回值

包含命令列的字串。 值包括從回應檔中取得的引數，以及來自 CL、\_CL\_、連結和 \_連結\_等環境變數。

::: moniker-end

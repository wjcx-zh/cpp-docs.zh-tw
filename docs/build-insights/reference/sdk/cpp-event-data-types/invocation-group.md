---
title: 呼叫元件
description: C++生成見解 SDK 調用組類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324696"
---
# <a name="invocationgroup-class"></a>呼叫元件

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`InvocationGroup`類與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn 會員函數一](../functions/match-event-stack-in-member-function.md)起使用。 使用它符合包含[「編譯器](../event-table.md#compiler)」和[「連結」](../event-table.md#linker)事件組合的群組。

## <a name="syntax"></a>語法

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>成員

除了從[\<EEventGroup\>呼叫](event-group.md)基類別繼承的成員一`InvocationGroup`起, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[呼叫群組](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>呼叫群組

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>參數

*群組*\
包含[「編譯器」](../event-table.md#compiler)和[「連結」](../event-table.md#linker)事件組合的群組。

::: moniker-end

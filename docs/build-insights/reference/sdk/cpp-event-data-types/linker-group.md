---
title: 連結器組類別
description: C++生成見解 SDK 連結器組類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324652"
---
# <a name="linkergroup-class"></a>連結器組類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`LinkerGroup`類與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn 會員函數一](../functions/match-event-stack-in-member-function.md)起使用。 使用它符合[LINKER](../event-table.md#linker)事件群組。

## <a name="syntax"></a>語法

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>成員

除了從[\<EEventGroup\>Linker](event-group.md)基項繼承的成員`LinkerGroup`一起, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[連結器組](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>連結器組

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>參數

*群組*\
一組[LINKER](../event-table.md#linker)事件。

::: moniker-end

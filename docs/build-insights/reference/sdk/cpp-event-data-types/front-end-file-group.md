---
title: 前端檔案組別
description: C++生成見解 SDK 前端檔組類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324766"
---
# <a name="frontendfilegroup-class"></a>前端檔案組別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`FrontEndFileGroup`類與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn 會員函數一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配[FRONT_END_FILE](../event-table.md#front-end-file)事件組。

## <a name="syntax"></a>語法

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>成員

除了從[其 EventGroup\<FrontEndFile\>](event-group.md)基類繼承的成員一起,該`FrontEndFileGroup`類別還包含以下成員:

### <a name="constructors"></a>建構函式

[前端檔案群組](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>前端檔案群組

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>參數

*群組*\
一組[FRONT_END_FILE](../event-table.md#front-end-file)事件。

::: moniker-end

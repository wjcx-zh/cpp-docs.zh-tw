---
title: FrontEndFileGroup 類別
description: C++ BUILD Insights SDK FrontEndFileGroup 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333325"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndFileGroup` 類別與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 用來比對[FRONT_END_FILE](../event-table.md#front-end-file)事件的群組。

## <a name="syntax"></a>語法

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>成員

除了從其[EventGroup\<FrontEndFile\>](event-group.md)基類繼承的成員之外，`FrontEndFileGroup` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>參數

*群組*\
一組[FRONT_END_FILE](../event-table.md#front-end-file)事件。

::: moniker-end

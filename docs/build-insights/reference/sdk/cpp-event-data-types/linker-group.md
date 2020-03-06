---
title: LinkerGroup 類別
description: C++ BUILD Insights SDK LinkerGroup 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333206"
---
# <a name="linkergroup-class"></a>LinkerGroup 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`LinkerGroup` 類別與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 用來比對[連結器](../event-table.md#linker)事件的群組。

## <a name="syntax"></a>語法

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>成員

除了其[EventGroup\<連結器](event-group.md)的繼承成員\>基類，`LinkerGroup` 類別包含下列成員：

### <a name="constructors"></a>建構函式

[LinkerGroup](#linker-group)

## <a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>參數

*群組*\
[連結器](../event-table.md#linker)事件的群組。

::: moniker-end

---
title: InvocationGroup 類別
description: C++ BUILD Insights SDK InvocationGroup 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333234"
---
# <a name="invocationgroup-class"></a>InvocationGroup 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`InvocationGroup` 類別與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對包含[編譯器](../event-table.md#compiler)和[連結器](../event-table.md#linker)事件混合的群組。

## <a name="syntax"></a>語法

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>成員

除了來自其 EventGroup 的繼承成員[\<調用\>](event-group.md)基類，`InvocationGroup` 類別包含下列成員：

### <a name="constructors"></a>建構函式

[InvocationGroup](#invocation-group)

## <a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>參數

*群組*\
包含[編譯器](../event-table.md#compiler)和[連結器](../event-table.md#linker)事件混合的群組。

::: moniker-end

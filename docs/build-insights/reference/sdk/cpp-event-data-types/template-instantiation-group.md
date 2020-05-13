---
title: 樣本即時組類別
description: C++生成見解 SDK 範本即時組類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 18dd48219c7c68ce152c381eb505fe37b19ec8dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324265"
---
# <a name="templateinstantiationgroup-class"></a>樣本即時組類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`TemplateInstantiationGroup`類與[MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackIn 會員函數一](../functions/match-event-stack-in-member-function.md)起使用。 使用它匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件組。

## <a name="syntax"></a>語法

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>成員

除了從[事件\<組 樣本實體化\>](event-group.md)基類繼承的成員一起`TemplateInstantiationGroup`, 該類包含以下成員:

### <a name="constructors"></a>建構函式

[樣本即時群組](#template-instantiation-group)

## <a name="templateinstantiationgroup"></a><a name="template-instantiation-group"></a>樣本即時群組

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>參數

*群組*\
一組[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end

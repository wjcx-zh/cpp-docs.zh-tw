---
title: ForceInlinee 類別
description: C++ BUILD Insights SDK ForceInlinee 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333332"
---
# <a name="forceinlinee-class"></a>ForceInlinee 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`ForceInlinee` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="syntax"></a>語法

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>成員

除了來自其[SimpleEvent](simple-event.md)基類的繼承成員之外，`ForceInlinee` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[名稱](#name)
[大小](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

強制內嵌函數的名稱，以 UTF-8 編碼。

## <a name="size"></a>容量

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>傳回值

強制內嵌函數的大小，做為中繼指令計數。

::: moniker-end

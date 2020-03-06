---
title: C1DLL 類別
description: C++ BUILD INSIGHTS SDK C1DLL 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C1DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f843e7dcd14dc9e9649317933008b575ff4eddf0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333528"
---
# <a name="c1dll-class"></a>C1DLL 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`C1DLL` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[C1_DLL](../event-table.md#c1-dll)事件。

## <a name="syntax"></a>語法

```cpp
class C1DLL : public Activity
{
public:
    C1DLL(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了來自其[Activity](activity.md)基類的繼承成員之外，`C1DLL` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[C1DLL](#c1-dll)

## <a name="c1-dll"></a>C1DLL

```cpp
C1DLL(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[C1_DLL](../event-table.md#c1-dll)事件。

::: moniker-end

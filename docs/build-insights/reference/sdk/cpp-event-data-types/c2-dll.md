---
title: C2DLL 類別
description: C++ BUILD INSIGHTS SDK C2DLL 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9a8ae7e8cd2d4d379865a9a7a388a6204eb9f173
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333493"
---
# <a name="c2dll-class"></a>C2DLL 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`C2DLL` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[C2_DLL](../event-table.md#c2-dll)事件。

## <a name="syntax"></a>語法

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了來自其[Activity](activity.md)基類的繼承成員之外，`C2DLL` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[C2DLL](#c2-dll)

## <a name="c2-dll"></a>C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[C2_DLL](../event-table.md#c2-dll)事件。

::: moniker-end

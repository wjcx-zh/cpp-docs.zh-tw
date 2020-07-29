---
title: MatchEvent
description: C + + Build Insights SDK MatchEvent 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8ec2c6bfcacf28998058dc66b5f363fbf1ea5d70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224106"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

函 `MatchEvent` 式可用來比對事件與事件種類清單。 如果事件符合清單中的類型，則會將它轉送至處理常式，以進行進一步的處理。

## <a name="syntax"></a>語法

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>參數

*TEvent*\
您想要比對的第一個事件種類。

*TEvents*\
您想要比對的其餘事件種類。

*TCallable*\
支援的類型 `operator()` 。 如需哪些引數會傳遞給這個運算子的詳細資訊，請參閱可呼叫*的參數描述*。

*TExtraArgs*\
傳遞至的額外引數類型 `MatchEvent` 。

*發生*\
要比對*TEvent*和*TEvents*所描述之事件種類的事件。

*多次*\
`MatchEvent`在成功比對事件與*TEvent*和*TEvents*所描述的任何事件*類型後，* 叫用可呼叫。 傳遞*至可*呼叫的第一個引數是相符事件種類的 r 值。 *ExtraArgs*參數套件在可呼叫的剩餘參數中是完美轉送*的。*  

*extraArgs*\
引數，會與相符的事件種類一起完美*轉寄至可*呼叫。

### <a name="return-value"></a>傳回值

**`bool`** 如果比對成功，則值為 **`true`** ，否則為 **`false`** 。

## <a name="remarks"></a>備註

系統會從*capture 類別*清單中選取要用於*TEvent*和*TEvents*參數的事件種類。 如需事件清單，以及您可以用來比對的 capture 類別，請參閱[事件資料表](../event-table.md)。

## <a name="example"></a>範例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end

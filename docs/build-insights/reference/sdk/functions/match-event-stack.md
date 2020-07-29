---
title: MatchEventStack
description: C + + Build Insights SDK MatchEventStack 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae476c402c3ea0cad558ce41a979b4233e0f1dd3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224119"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStack`函數是用來比對事件堆疊與特定的事件階層。 符合的階層會轉送至處理常式，以供進一步處理。 若要深入瞭解事件、事件堆疊和階層，請參閱[事件資料表](../event-table.md)。

## <a name="syntax"></a>語法

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>參數

*TEvent*\
要在事件堆疊中符合的 eldest 父系型別。

*TEvents*\
您想要在事件堆疊中比對的其餘類型。

*TCallable*\
支援的類型 `operator()` 。 如需哪些引數會傳遞給這個運算子的詳細資訊，請參閱可呼叫*的參數描述*。

*TExtraArgs*\
傳遞至之額外引數的類型 `MatchEventStack` 。

*eventStack*\
要比對*TEvent*和*TEvents*所描述之事件種類階層的事件堆疊。

*多次*\
成功比對事件堆疊與*TEvent*和*TEvents*所描述的事件種類階層架構時，會叫用可呼叫的 `MatchEventStack` 。 *callable* 它會針對事件階層中的每個型*別，將一個 r*值引數傳遞給。 *ExtraArgs*參數套件在可呼叫的剩餘參數中是完美轉送*的。*

*extraArgs*\
引數，會與相符的事件種類一起完美*轉寄至可*呼叫。

### <a name="return-value"></a>傳回值

**`bool`** 如果比對成功，則值為 **`true`** ，否則為 **`false`** 。

## <a name="remarks"></a>備註

*EventStack*中的最後一個事件一律會與 [串連的 \[ *TEvent*]、[ *TEvents* ] [類型] 清單中的最後一個專案進行比對。 \] 除了最後一個以外，所有其他*TEvent*和*TEvents*專案都可以符合*eventStack*中的任何位置，但前提是它們的順序相同。

系統會從*capture 類別*清單中選取要用於*TEvent*和*TEvents*參數的事件種類。 如需事件清單，以及您可以用來比對的 capture 類別，請參閱[事件資料表](../event-table.md)。

## <a name="example"></a>範例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end

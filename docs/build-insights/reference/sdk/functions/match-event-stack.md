---
title: 符合事件堆疊
description: C++生成見解 SDK 匹配事件堆疊函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323866"
---
# <a name="matcheventstack"></a>符合事件堆疊

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MatchEventStack`函數用於將事件堆疊與特定事件層次結構匹配。 匹配的層次結構將轉發到處理程式以進行進一步處理。 要瞭解有關事件、事件堆疊和層次結構的更多資訊,請參閱[事件表](../event-table.md)。

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
要在事件堆疊中匹配的父項的類型。

*TEvents*\
您希望在事件堆疊中匹配的剩餘類型。

*可呼叫*\
支援`operator()`的類型。 有關哪些參數傳遞給此運算符的詳細資訊,請參閱*可調用*參數說明。

*TExtraArgs*\
傳遞給的額外參數的類型`MatchEventStack`。

*事件堆疊*\
要與*TEvent*和*TEvents*描述的事件類型層次結構匹配的事件堆疊。

*呼叫*\
成功將事件堆疊與*TEvent*與*TEvent*描述的`MatchEventStack`事件類型層次結構 符合後,將呼叫*可呼叫*。 它將事件層次結構中每種類型的*可調用*一個 r 值參數傳遞給。 在*可呼叫*的剩餘參數中,*額外的 Args*參數套件是完美的轉發。

*額外阿格*\
與匹配的事件類型一起被完全轉發到*可呼叫*的參數。

### <a name="return-value"></a>傳回值

如果匹配成功,則**為 true**的**bool**值,否則為**false。**

## <a name="remarks"></a>備註

*事件堆疊*中的最後一個事件始終與串\[聯*TEvent、TEvents...* *TEvents...*\]類型清單。 所有其他*TEvent*和*TEvents*條目可以匹配*事件堆疊*中的任何位置,但最後一個位置除外,前提是它們的順序相同。

用於*TEvent*和*TEvents*參數的事件類型是從*捕獲類*清單中選擇的。 有關可用於符合的事件和擷取類的清單,請參閱[事件表](../event-table.md)。

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

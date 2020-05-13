---
title: 符合事件
description: C++生成見解 SDK 匹配事件函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323861"
---
# <a name="matchevent"></a>符合事件

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MatchEvent`函數用於將事件與事件類型清單匹配。 如果事件與清單中的類型匹配,則該事件將轉發到處理程式以進行進一步處理。

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
要匹配的第一個事件類型。

*TEvents*\
要匹配的剩餘事件類型。

*可呼叫*\
支援`operator()`的類型。 有關哪些參數傳遞給此運算符的詳細資訊,請參閱*可調用*參數說明。

*TExtraArgs*\
傳遞給的額外參數的類型`MatchEvent`。

*事件*\
要與*TEvent*和*TEvents*描述的事件類型匹配的事件。

*呼叫*\
`MatchEvent`在成功將事件與*TEvent*與*TEvent*描述的任何事件類型符合後*呼叫可呼叫*。 傳遞給*可呼叫*的第一個參數是匹配事件類型的 r 值。 在*可呼叫*的剩餘參數中,*額外的 Args*參數套件是完美的轉發。  

*額外阿格*\
與匹配的事件類型一起被完全轉發到*可呼叫*的參數。

### <a name="return-value"></a>傳回值

如果匹配成功,則為**true**的**bool**值,否則為**false。**

## <a name="remarks"></a>備註

用於*TEvent*和*TEvents*參數的事件類型是從*捕獲類*清單中選擇的。 有關可用於符合的事件和擷取類的清單,請參閱[事件表](../event-table.md)。

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

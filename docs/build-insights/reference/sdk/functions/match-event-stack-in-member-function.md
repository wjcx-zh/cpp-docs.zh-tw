---
title: 符合事件堆疊成員函數
description: C++生成見解 SDK 匹配事件Stackin成員函數函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323890"
---
# <a name="matcheventstackinmemberfunction"></a>符合事件堆疊成員函數

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MatchEventStackInMemberFunction`函數用於將事件堆疊與特定事件層次結構匹配,由成員函數的參數清單描述。 匹配的層次結構將轉發到成員函數以進行進一步處理。 要瞭解有關事件、事件堆疊和層次結構的更多資訊,請參閱[事件表](../event-table.md)。

## <a name="syntax"></a>語法

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>參數

*T 介面*\
包含成員函數的類型。

*T返回*\
成員函數的返回類型。

*T1*, ..., *T10*\
描述要匹配的事件層次結構的類型。

*特特帕姆斯*\
成員函數接受的額外參數的類型和事件層次結構類型。

*TExtraArgs*\
傳遞給的額外參數的類型`MatchEventStackInMemberFunction`。

*事件堆疊*\
要與 T1 到*T10**T10*描述的事件類型 層次結構匹配的事件堆疊。

*物件Ptr*\
指向調用*成員Func*的物件的指標。

*成員豐奇*\
描述要匹配的事件類型層次結構的成員函數。

*額外阿格*\
與事件類型層次結構參數一起完美轉發到*成員Func*的參數。

### <a name="return-value"></a>傳回值

如果匹配成功,則**為 true**的**bool**值,否則為**false。**

## <a name="remarks"></a>備註

*事件堆疊*中的最後一個事件始終與要匹配的事件類型層次結構中的最後一個條目匹配。 事件類型層次結構中的所有其他類型的都可以匹配*事件堆疊*中的任何位置,但最後一個位置除外,前提是它們的順序相同。

用於 T1 到*T10*參數的*T10*事件類型是從*捕獲類*清單中選擇的。 有關可用於符合的事件和擷取類的清單,請參閱[事件表](../event-table.md)。

## <a name="example"></a>範例

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end

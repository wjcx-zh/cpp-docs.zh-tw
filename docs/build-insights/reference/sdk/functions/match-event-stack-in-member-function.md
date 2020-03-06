---
title: MatchEventStackInMemberFunction
description: C++ BUILD Insights SDK MatchEventStackInMemberFunction 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332786"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStackInMemberFunction` 函式是用來比對事件堆疊與特定事件階層架構（由成員函式的參數清單所描述）。 相符的階層會轉送到成員函式以供進一步處理。 若要深入瞭解事件、事件堆疊和階層，請參閱[事件資料表](../event-table.md)。

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

*TInterface*\
包含成員函式的類型。

*TReturn*\
成員函式的傳回型別。

*T1*、...、 *T10*\
描述要比對之事件階層的類型。

*TExtraParams*\
成員函式所接受的額外參數類型，以及事件階層類型。

*TExtraArgs*\
傳遞至 `MatchEventStackInMemberFunction`之額外引數的類型。

*eventStack*\
要比對*T1*到*T10*所描述之事件種類階層的事件堆疊。

*objectPtr*\
呼叫*memberFunc*之物件的指標。

*memberFunc*\
描述要比對之事件種類階層的成員函式。

*extraArgs*\
與事件種類階層參數一起完美轉寄至*memberFunc*的引數。

### <a name="return-value"></a>傳回值

**布林**值，如果比對成功，則為**true** ，否則為**false** 。

## <a name="remarks"></a>備註

*EventStack*中的最後一個事件一律會與事件種類階層中的最後一個專案相符，以符合。 事件種類階層中的所有其他類型都可以比對*eventStack*中的任何位置（最後一個除外），前提是它們的順序相同。

您可以從*capture 類別*清單中選取要用於*T1*到*T10*參數的事件種類。 如需事件清單，以及您可以用來比對的 capture 類別，請參閱[事件資料表](../event-table.md)。

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

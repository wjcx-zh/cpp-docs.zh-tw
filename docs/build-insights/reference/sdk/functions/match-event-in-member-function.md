---
title: MatchEventInMemberFunction
description: C + + Build Insights SDK MatchEventInMemberFunction 函數參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d3fdc015b0744cb5d0f98a1c9025343b93489ed9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224145"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

C + + Build Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventInMemberFunction`函數是用來比對事件與成員函式的第一個參數所描述的類型。 符合的事件會轉送到成員函式以供進一步處理。

## <a name="syntax"></a>語法

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>參數

*TInterface*\
包含成員函式的類型。

*TReturn*\
成員函式的傳回型別。

*TEvent*\
要比對之事件的類型。

*TExtraParams*\
成員函式所接受之額外參數的類型，以及要比對的事件種類。

*TExtraArgs*\
傳遞至的額外引數類型 `MatchEventInMemberFunction` 。

*發生*\
要比對*TEvent*所描述之事件種類的事件。

*objectPtr*\
呼叫*memberFunc*之物件的指標。

*memberFunc*\
描述要比對之事件種類的成員函式。

*extraArgs*\
與事件種類參數完美地轉送至*memberFunc*的引數。

### <a name="return-value"></a>傳回值

**`bool`** 如果比對成功，則值為 **`true`** ，否則為 **`false`** 。

## <a name="remarks"></a>備註

您可以從*capture 類別*清單中選取要用於*TEvent*參數的事件種類。 如需事件清單，以及您可以用來比對的 capture 類別，請參閱[事件資料表](../event-table.md)。

## <a name="example"></a>範例

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end

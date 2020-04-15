---
title: 符合事件成員函數
description: C++生成見解 SDK 匹配事件成員函數函數引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323904"
---
# <a name="matcheventinmemberfunction"></a>符合事件成員函數

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`MatchEventInMemberFunction`函數用於將事件與成員函數的第一個參數描述的類型匹配。 匹配的事件將轉發到成員函數以進行進一步處理。

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

*T 介面*\
包含成員函數的類型。

*T返回*\
成員函數的返回類型。

*TEvent*\
要匹配的事件的類型。

*特特帕姆斯*\
成員函數接受的額外參數的類型以及要匹配的事件類型。

*TExtraArgs*\
傳遞給的額外參數的類型`MatchEventInMemberFunction`。

*事件*\
要與*TEvent*描述的事件類型匹配的事件。

*物件Ptr*\
指向調用*成員Func*的物件的指標。

*成員豐奇*\
描述要匹配的事件類型的成員函數。

*額外阿格*\
與事件類型參數一起完美轉發到*成員Func*的參數。

### <a name="return-value"></a>傳回值

如果匹配成功,則**為 true**的**bool**值,否則為**false。**

## <a name="remarks"></a>備註

可用於*TEvent*參數的事件類型可以從*捕獲類*清單中選擇。 有關可用於符合的事件和擷取類的清單,請參閱[事件表](../event-table.md)。

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

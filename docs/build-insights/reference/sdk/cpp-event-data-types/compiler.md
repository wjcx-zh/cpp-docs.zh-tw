---
title: 編譯器類
description: C++生成見解 SDK 編譯器類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325034"
---
# <a name="compiler-class"></a>編譯器類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Compiler`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[「編譯器」](../event-table.md#compiler)事件。

## <a name="syntax"></a>語法

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>成員

除了從其[調用](invocation.md)基類繼承的成員一`Compiler`起, 該類還包含以下成員:

### <a name="constructors"></a>建構函式

[編譯器](#compiler)

## <a name="compiler"></a><a name="compiler"></a>編譯 器

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[一個編譯器](../event-table.md#compiler)事件。

::: moniker-end

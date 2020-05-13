---
title: 環境變數類
description: C++生成見解 SDK 環境變數類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325010"
---
# <a name="environmentvariable-class"></a>環境變數類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`EnvironmentVariable`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="syntax"></a>語法

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>成員

除了其[SimpleEvent](simple-event.md)基類別中繼承的成員`EnvironmentVariable`外, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>函式

[名稱](#name)
[值](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>環境變數

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="name"></a><a name="name"></a>名稱

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>傳回值

環境變數的名稱。

## <a name="value"></a><a name="value"></a> 值

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>傳回值

環境變數的值。

::: moniker-end

---
title: 調用類
description: C++生成見解 SDK 調用類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fcb087d46ea445251b0108f811545a44c26f421e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324635"
---
# <a name="invocation-class"></a>調用類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Invocation`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它符合[「編譯器](../event-table.md#compiler)」或[「連結」](../event-table.md#linker)事件。

## <a name="syntax"></a>語法

```cpp
class Invocation : public Activity
{
    const INVOCATION_DATA* data_;

public:
    enum class Type
    {
        CL      = MSVC_TOOL_CODE_CL,
        LINK    = MSVC_TOOL_CODE_LINK
    };

    Invocation(const RawEvent& event);

    Type             Type() const;
    const char*      ToolVersionString() const;
    const wchar_t*   WorkingDirectory() const;
    const wchar_t*   ToolPath() const;

    const INVOCATION_VERSION_DATA& ToolVersion() const;
};
```

## <a name="members"></a>成員

除了從[其活動](activity.md)基類繼承的成員`Invocation`外, 該類還包含以下成員:

### <a name="constructors"></a>建構函式

[引動過程](#invocation)

### <a name="functions"></a>函式

[工具路徑](#tool-path)
[工具版本](#tool-version)
[版本字串](#tool-version-string)
[類型工作](#type)
[目錄](#working-directory)

## <a name="invocation"></a><a name="invocation"></a>呼叫

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[一個編譯器](../event-table.md#compiler)或[連結器](../event-table.md#linker)事件。

## <a name="toolpath"></a><a name="tool-path"></a>工具路徑

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>傳回值

調用的工具的絕對路徑。

## <a name="toolversion"></a><a name="tool-version"></a>工具版本

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>傳回值

作為[INVOCATION_VERSION_DATA引用](../c-event-data-types/invocation-version-data-struct.md)而調用的工具的版本。

## <a name="toolversionstring"></a><a name="tool-version-string"></a>工具版本字串

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>傳回值

作為 ANSI 字串調用的工具的版本。

## <a name="type"></a><a name="type"></a> 類型

```cpp
Type Type() const;
```

### <a name="return-value"></a>傳回值

指示被調用工具的代碼。

## <a name="workingdirectory"></a><a name="working-directory"></a>工作目錄

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>傳回值

呼叫工具的目錄的絕對路徑。

::: moniker-end

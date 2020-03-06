---
title: 調用類別
description: C++ BUILD Insights SDK 調用類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Invocation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c4698300a3eeaf77210ad74f84b0c0cd219b457
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333227"
---
# <a name="invocation-class"></a>調用類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`Invocation` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[編譯器](../event-table.md#compiler)或[連結器](../event-table.md#linker)事件。

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

除了來自其[Activity](activity.md)基類的繼承成員之外，`Invocation` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[引動過程](#invocation)

### <a name="functions"></a>Functions


[toolversion 設](#tool-version)
[ToolVersionString](#tool-version-string)
[類型](#type)
[WorkingDirectory](#working-directory)的[刀具路徑](#tool-path)

## <a name="invocation"></a>啟動

```cpp
Invocation(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[編譯器](../event-table.md#compiler)或[連結器](../event-table.md#linker)事件。

## <a name="tool-path"></a>作用

```cpp
const wchar_t* ToolPath() const;
```

### <a name="return-value"></a>傳回值

所叫用之工具的絕對路徑。

## <a name="tool-version"></a>Toolversion 設

```cpp
const INVOCATION_VERSION_DATA& ToolVersion() const;
```

### <a name="return-value"></a>傳回值

已叫用的工具版本，做為[INVOCATION_VERSION_DATA](../c-event-data-types/invocation-version-data-struct.md)參考。

## <a name="tool-version-string"></a>ToolVersionString

```cpp
const char* ToolVersionString() const;
```

### <a name="return-value"></a>傳回值

已叫用的工具版本，表示為 ANSI 字串。

## <a name="type"></a>型

```cpp
Type Type() const;
```

### <a name="return-value"></a>傳回值

表示已叫用之工具的程式碼。

## <a name="working-directory"></a>WorkingDirectory

```cpp
const wchar_t* WorkingDirectory() const;
```

### <a name="return-value"></a>傳回值

叫用工具所在目錄的絕對路徑。

::: moniker-end

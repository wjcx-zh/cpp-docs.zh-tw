---
title: 編譯器Pass 類別
description: C++生成見解 SDK 編譯器傳遞類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 11af981b647d5183f88dad024d90c0ef4f8a28bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325048"
---
# <a name="compilerpass-class"></a>編譯器Pass 類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`CompilerPass`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="syntax"></a>語法

```cpp
class CompilerPass : public Activity
{
public:
    enum class PassCode
    {
        FRONT_END,
        BACK_END
    };

    CompilerPass(const RawEvent& event);

    PassCode       PassCode() const;
    const wchar_t* InputSourcePath() const;
    const wchar_t* OutputObjectPath() const;
};
```

## <a name="members"></a>成員

除了從[其活動](activity.md)基類繼承的成員`CompilerPass`外, 該類還包含以下成員:

### <a name="constructors"></a>建構函式

[編譯器通行證](#compiler-pass)

### <a name="enums"></a>列舉

#### <a name="passcode"></a>密碼

|||
|-|-|
|FRONT_END|前端通道。|
|BACK_END|後端傳遞。|

### <a name="functions"></a>函式

[輸入來源路徑](#input-source-path)\
[輸出物件路徑](#output-object-path)\
[密碼](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a>編譯器通行證

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="inputsourcepath"></a><a name="input-source-path"></a>輸入來源路徑

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>傳回值

此編譯器處理的輸入源文件的絕對路徑通過。

## <a name="outputobjectpath"></a><a name="output-object-path"></a>輸出物件路徑

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>傳回值

此編譯器生成的輸出物件文件的絕對路徑通過。

## <a name="passcode"></a><a name="pass-code"></a>密碼

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>傳回值

指示哪個編譯器傳遞由此編譯器Pass 物件表示的代碼。

::: moniker-end

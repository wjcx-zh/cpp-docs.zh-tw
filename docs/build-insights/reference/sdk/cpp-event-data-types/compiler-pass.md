---
title: CompilerPass 類別
description: C++ BUILD Insights SDK CompilerPass 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c2fa1c2c4be8aaf5bec77b383f93a4b033ca8e3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333472"
---
# <a name="compilerpass-class"></a>CompilerPass 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

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

除了來自其[Activity](activity.md)基類的繼承成員之外，`CompilerPass` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[CompilerPass](#compiler-pass)

### <a name="enums"></a>列舉

#### <a name="passcode"></a>碼

|||
|-|-|
|FRONT_END|前端階段。|
|BACK_END|後端傳遞。|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[密碼](#pass-code)\

## <a name="compiler-pass"></a>CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="input-source-path"></a>InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>傳回值

這個編譯器傳遞所處理之輸入來源檔案的絕對路徑。

## <a name="output-object-path"></a>OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>傳回值

這個編譯器傳遞所產生之輸出物件檔案的絕對路徑。

## <a name="pass-code"></a>碼

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>傳回值

表示這個 CompilerPass 物件所表示之編譯器傳遞的程式碼。

::: moniker-end

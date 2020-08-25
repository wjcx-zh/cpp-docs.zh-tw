---
title: CompilerPass 類別
description: C + + Build Insights SDK CompilerPass 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CompilerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 054bdf75dcfca42b8c202565fb44df671f17f912
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831615"
---
# <a name="compilerpass-class"></a>CompilerPass 類別

::: moniker range="<=vs-2015"

C + + Build Insights SDK 符合 Visual Studio 2017 和更新版本的相容性。 若要查看這些版本的檔，請將此文章的 Visual Studio **版本** 選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 您可在此頁面的目錄頂端找到此檔案。

::: moniker-end
::: moniker range=">=vs-2017"

`CompilerPass`類別可與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 您可以使用它來比對 [BACK_END_PASS](../event-table.md#back-end-pass) 或 [FRONT_END_PASS](../event-table.md#front-end-pass) 事件。

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

類別以及其 [活動](activity.md) 基類的繼承成員， `CompilerPass` 包含下列成員：

### <a name="constructors"></a>建構函式

[CompilerPass](#compiler-pass)

### <a name="enums"></a>列舉

#### <a name="passcode"></a>密碼

|值|描述|
|-|-|
|FRONT_END|前端傳遞。|
|BACK_END|後端傳遞。|

### <a name="functions"></a>Functions

[InputSourcePath](#input-source-path)\
[OutputObjectPath](#output-object-path)\
[密碼](#pass-code)\

## <a name="compilerpass"></a><a name="compiler-pass"></a> CompilerPass

```cpp
CompilerPass(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[BACK_END_PASS](../event-table.md#back-end-pass)或[FRONT_END_PASS](../event-table.md#front-end-pass)事件。

## <a name="inputsourcepath"></a><a name="input-source-path"></a> InputSourcePath

```cpp
const wchar_t* InputSourcePath() const;
```

### <a name="return-value"></a>傳回值

此編譯器傳遞所處理之輸入來源檔案的絕對路徑。

## <a name="outputobjectpath"></a><a name="output-object-path"></a> OutputObjectPath

```cpp
const wchar_t* OutputObjectPath() const;
```

### <a name="return-value"></a>傳回值

此編譯器傳遞所產生之輸出物件檔案的絕對路徑。

## <a name="passcode"></a><a name="pass-code"></a> 密碼

```cpp
PassCode PassCode() const;
```

### <a name="return-value"></a>傳回值

指出由這個 CompilerPass 物件所代表之編譯器傳遞的程式碼。

::: moniker-end

---
title: EnvironmentVariable 類別
description: C++ BUILD Insights SDK EnvironmentVariable 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 19e9278e76fb2116dac30a0e790fba86c6c56484
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333437"
---
# <a name="environmentvariable-class"></a>EnvironmentVariable 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`EnvironmentVariable` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

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

## <a name="members"></a>Members

除了來自其[SimpleEvent](simple-event.md)基類的繼承成員之外，`EnvironmentVariable` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[EnvironmentVariable](#environment-variable)

### <a name="functions"></a>Functions

[「名稱」](#name)
[「值」](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>EnvironmentVariable

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[ENVIRONMENT_VARIABLE](../event-table.md#environment-variable)事件。

## <a name="name"></a><a name="name"></a> Name

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>傳回值

環境變數的名稱。

## <a name="value"></a><a name="value"></a>Value

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>傳回值

環境變數的值。

::: moniker-end

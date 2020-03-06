---
title: Function 類別
description: C++ BUILD Insights SDK 函數類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333255"
---
# <a name="function-class"></a>Function 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`Function` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[函數](../event-table.md#function)事件。

## <a name="syntax"></a>語法

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>成員

除了來自其[Activity](activity.md)基類的繼承成員之外，`Function` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[Function](#function)

### <a name="functions"></a>Functions

[名稱](#name)

## <a name="function"></a>函數

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[函數](../event-table.md#function)事件。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

函數的名稱，以 UTF-8 編碼。

::: moniker-end

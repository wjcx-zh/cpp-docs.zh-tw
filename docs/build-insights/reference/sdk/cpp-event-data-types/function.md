---
title: 函式
description: C++生成見解 SDK 函數類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 69acbe4d6630de37120aec89a24a9f33d447009e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324715"
---
# <a name="function-class"></a>函式

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`Function`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[功能](../event-table.md#function)事件。

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

除了從[其活動](activity.md)基類繼承的成員`Function`外, 該類還包含以下成員:

### <a name="constructors"></a>建構函式

[函數](#function)

### <a name="functions"></a>函式

[名稱](#name)

## <a name="function"></a><a name="function"></a>功能

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[一個功能](../event-table.md#function)事件。

## <a name="name"></a><a name="name"></a>名稱

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

函數的名稱,在UTF-8中編碼。

::: moniker-end

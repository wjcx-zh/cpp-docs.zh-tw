---
title: 力內聯類
description: C++構建見解 SDK 強制內聯類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324788"
---
# <a name="forceinlinee-class"></a>力內聯類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`ForceInlinee`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="syntax"></a>語法

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>成員

除了其[SimpleEvent](simple-event.md)基類別中繼承的成員`ForceInlinee`外, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[力因內](#force-inlinee)

### <a name="functions"></a>函式

[名稱](#name)
[大小](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a>力因內

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[FORCE_INLINEE](../event-table.md#force-inlinee)事件。

## <a name="name"></a><a name="name"></a>名稱

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

力內聯函數的名稱,在UTF-8 中編碼。

## <a name="size"></a><a name="size"></a> 大小

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>傳回值

力內聯函數的大小,作為中間指令計數。

::: moniker-end

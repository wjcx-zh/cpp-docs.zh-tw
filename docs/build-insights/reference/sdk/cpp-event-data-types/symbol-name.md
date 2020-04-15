---
title: 符號名稱類別
description: C++生成見解 SDK 符號名稱類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324347"
---
# <a name="symbolname-class"></a>符號名稱類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`SymbolName`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[SYMBOL_NAME](../event-table.md#symbol-name)事件。

## <a name="syntax"></a>語法

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>成員

除了其[SimpleEvent](simple-event.md)基類別中繼承的成員`SymbolName`外, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[符號名稱](#symbol-name)

### <a name="functions"></a>函式

[金鑰](#key)
[名稱](#name)

## <a name="key"></a><a name="key"></a>關鍵

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>傳回值

此符號表示的類型的數字識別碼。 此標識碼在編譯器前端傳遞中是唯一的。

## <a name="name"></a><a name="name"></a>名稱

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

符號表示的類型的名稱,以 UTF-8 編碼。

## <a name="symbolname"></a><a name="symbol-name"></a>符號名稱

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[SYMBOL_NAME](../event-table.md#symbol-name)事件。

::: moniker-end

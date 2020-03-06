---
title: SymbolName 類別
description: C++ BUILD Insights SDK SymbolName 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b5e9a9b22db99c099b9f7dc1813fb335358a83e8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332996"
---
# <a name="symbolname-class"></a>SymbolName 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`SymbolName` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[SYMBOL_NAME](../event-table.md#symbol-name)事件。

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

除了來自其[SimpleEvent](simple-event.md)基類的繼承成員之外，`SymbolName` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[SymbolName](#symbol-name)

### <a name="functions"></a>Functions

[金鑰](#key)
[名稱](#name)

## <a name="key"></a>擊鍵

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>傳回值

這個符號所表示之類型的數值識別碼。 這個識別碼在編譯器前端階段中是唯一的。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>傳回值

以 UTF-8 編碼的符號所代表的類型名稱。

## <a name="symbol-name"></a>SymbolName

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[SYMBOL_NAME](../event-table.md#symbol-name)事件。

::: moniker-end

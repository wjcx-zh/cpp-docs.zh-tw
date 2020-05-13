---
title: 檔案輸入類別
description: C++生成見解 SDK 檔輸入類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FileInput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 642236d3e67465ed38508cb24c8cd698ae880065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324801"
---
# <a name="fileinput-class"></a>檔案輸入類別

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`FileInput`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[FILE_INPUT](../event-table.md#file-input)事件。

## <a name="syntax"></a>語法

```cpp
class FileInput : public SimpleEvent
{
public:
    enum class Type
    {
        OTHER               = FILE_TYPE_CODE_OTHER,
        OBJ                 = FILE_TYPE_CODE_OBJ,
        EXECUTABLE_IMAGE    = FILE_TYPE_CODE_EXECUTABLE_IMAGE,
        LIB                 = FILE_TYPE_CODE_LIB,
        IMP_LIB             = FILE_TYPE_CODE_IMP_LIB,
        EXP                 = FILE_TYPE_CODE_EXP
    };

    FileInput(const RawEvent& event);

    const wchar_t* Path() const;
    Type           Type() const;
};
```

## <a name="members"></a>成員

除了其[SimpleEvent](simple-event.md)基類別中繼承的成員`FileInput`外, 該類別還包含以下成員:

### <a name="constructors"></a>建構函式

[檔案輸入](#file-input)

### <a name="functions"></a>函式

[路徑](#path)
[類型](#type)

## <a name="fileinput"></a><a name="file-input"></a>檔案輸入

```cpp
FileInput(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[FILE_INPUT](../event-table.md#file-input)事件。

## <a name="path"></a><a name="path"></a>路徑

```cpp
const wchar_t Path() const;
```

### <a name="return-value"></a>傳回值

輸入文件的絕對路徑。

## <a name="type"></a><a name="type"></a> 類型

```cpp
Type Type() const;
```

### <a name="return-value"></a>傳回值

描述輸入檔案類型的代碼。

::: moniker-end

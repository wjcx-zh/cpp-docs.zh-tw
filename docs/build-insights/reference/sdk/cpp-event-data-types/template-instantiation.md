---
title: 樣本即時化類
description: C++生成見解 SDK 範本即時性類引用。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324225"
---
# <a name="templateinstantiation-class"></a>樣本即時化類

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

該`TemplateInstantiation`類與[匹配事件](../functions/match-event.md)、[匹配事件在成員函數](../functions/match-event-in-member-function.md)、[匹配事件堆疊](../functions/match-event-stack.md)和[匹配事件堆疊功能](../functions/match-event-stack-in-member-function.md)一起使用。 使用它匹配[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

## <a name="syntax"></a>語法

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>成員

除了從[其活動](activity.md)基類繼承的成員`TemplateInstantiation`外, 該類還包含以下成員:

### <a name="constructors"></a>建構函式

[樣本即時性](#template-instantiation)

### <a name="functions"></a>函式

[類別](#kind)
[主樣本符號金鑰](#primary-template-symbol-key)
[專門化符號金鑰](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>種類

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>傳回值

描述已完成的範本實例化類型的代碼。

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>主樣本符號鍵

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>傳回值

專用範本類型的數值標識符。 此標識碼在編譯器前端傳遞中是唯一的。

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>專業化符號金鑰

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>傳回值

專門化類型的數值標識符。 此標識碼在編譯器前端傳遞中是唯一的。

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>樣本即時性

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>參數

*事件*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end

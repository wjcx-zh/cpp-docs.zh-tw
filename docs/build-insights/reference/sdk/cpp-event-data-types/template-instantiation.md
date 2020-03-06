---
title: TemplateInstantiation 類別
description: C++ BUILD Insights SDK TemplateInstantiation 類別參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2c94f8d3a4613e072c03f6dd4c846798d3d2122b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332968"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation 類別

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 與 Visual Studio 2017 和更新版本相容。 若要查看這些版本的檔，請將本文的 Visual Studio 版本選取器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。

::: moniker-end
::: moniker range=">=vs-2017"

`TemplateInstantiation` 類別會與[MatchEvent](../functions/match-event.md)、 [MatchEventInMemberFunction](../functions/match-event-in-member-function.md)、 [MatchEventStack](../functions/match-event-stack.md)和[MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md)函數搭配使用。 使用它來比對[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

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

除了來自其[Activity](activity.md)基類的繼承成員之外，`TemplateInstantiation` 類別還包含下列成員：

### <a name="constructors"></a>建構函式

[TemplateInstantiation](#template-instantiation)

### <a name="functions"></a>Functions

[種類](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpecializationSymbolKey](#specialization-symbol-key)

## <a name="kind"></a>常見

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>傳回值

描述已完成之範本具現化類型的程式碼。

## <a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>傳回值

特製化之範本類型的數值識別碼。 這個識別碼在編譯器前端階段中是唯一的。

## <a name="specialization-symbol-key"></a>SpecializationSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>傳回值

特製化類型的數值識別碼。 這個識別碼在編譯器前端階段中是唯一的。

## <a name="template-instantiation"></a>TemplateInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>參數

*event*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)事件。

::: moniker-end

---
title: TEMPLATE_INSTANTIATION_DATA結構
description: C++構建見解 SDK TEMPLATE_INSTANTIATION_DATA結構參考。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TEMPLATE_INSTANTIATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a38d19368e7c0a9912907f1da6e7a2e31ffe8d90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325324"
---
# <a name="template_instantiation_data-structure"></a>TEMPLATE_INSTANTIATION_DATA結構

::: moniker range="<=vs-2015"

C++構建見解 SDK 與 Visual Studio 2017 及以上版本相容。 要查看這些版本的文件,請將本文的 Visual Studio**版本**選擇器控制項設定為 Visual Studio 2017 或 Visual Studio 2019。 它位於此頁面的目錄頂部。

::: moniker-end
::: moniker range=">=vs-2017"

結構`TEMPLATE_INSTANTIATION_DATA`描述範本實例化。

## <a name="syntax"></a>語法

```cpp
typedef struct TEMPLATE_INSTANTIATION_DATA_TAG
{
    unsigned long long  SpecializationSymbolKey;
    unsigned long long  PrimaryTemplateSymbolKey;
    int                 KindCode;

} TEMPLATE_INSTANTIATION_DATA;
```

## <a name="members"></a>成員

|  |  |
|--|--|
| `SpecializationSymbolKey` | 範本專業化化類型的鍵。 此值在要分析的跟蹤中是唯一的。 |
| `PrimaryTemplateSymbolKey` | 專用主範本類型的鍵。 此值在要分析的跟蹤中是唯一的。 |
| `KindCode` | 範本實例化的類型。 有關詳細資訊,請參閱[TEMPLATE_INSTANTIATION_KIND_CODE](template-instantiation-kind-code-enum.md)。 |

## <a name="remarks"></a>備註

結構中的`TEMPLATE_INSTANTIATION_DATA`鍵在要分析的跟蹤中是唯一的。 但是,來自不同編譯器前端傳遞的兩個不同的密鑰可能指向兩種相同的類型。 使用`TEMPLATE_INSTANTIATION_DATA`來自多個編譯器前端傳遞的資訊時,請使用[SYMBOL_NAME](../event-table.md#symbol-name)事件來確定兩種類型是否相同。 `SymbolName`在編譯器前端傳遞結束時,在進行所有範本實例化後,將發出事件。

::: moniker-end
